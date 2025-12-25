
installation: pip install sqlmodel

**For Database Models**:

from sqlmodel import SQLModel, Field
from uuid import UUID, uuid4
import sqlalchemy as sa
from datetime import datetime, timezone, timedelta
from enum import Enum
from sqlalchemy.types import JSON

def now_utc():
    return datetime.now(timezone.utc)

def expires_at():
    return now_utc() + timedelta(days=7)

class UserStatus(str, Enum):
    CREATED = "CREATED"
    QUEUED = "QUEUED"

class User(SQLModel, table=True):
    __tablename__ = "users"
    id: int | None = Field(default=None, primary_key=True) # Creates an int primary key column with default value = None
    user_id: UUID = Field(default_factory=uuid4, primary_key=True) # Creates a UUID primary key
    token_hash: str = Field(sa_type=sa.String) # Creates a basic string column
    created_at: datetime = Field(default_factory=now_utc) # Creates a datetime column
    status: UserStatus = Field(sa_column=sa.Column(sa.String, sa.Enum(UserStatus))) # Creates an enum column with values "CREATED", "QUEUED"
    params: dict = Field(sa_column=sa.Column(JSON)) # Creates a column storing JSON objects
    token_expires_at: datetime = Field(default_factory=expires_at) # Sets datetime value to 7 days after row creation
    updated_at: datetime = Field(
        default_factory=now_utc,
        sa_column=sa.Column(sa.DateTime, default=now_utc, onupdate=now_utc) # Updates datetime value whenever row is updated
        )


from sqlmodel import Relationship

class Job(SQLModel, table=True):
    id: int = Field(primary_key=True)
    job_files: list["JobFiles"] = Relationship(back_populates="job") # Reverse relation to job_files

class JobFiles(SQLModel, table=True):
    id: int = Field(primary_key=True)
    job_id: int = Field(foreign_key="job.id") # Foreign key = 'id' from 'job'
    job: Job = Relationship((back_populates="job_files")) # Reverse relation to job
