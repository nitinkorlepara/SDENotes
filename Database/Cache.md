# Cache

- temporary storage with high read speeds.
- Cache invalidation

  - Write through -> updated data is written to both database and ache at the same time
  - Write Around -> updated data is written to database first and then to cache
  - write back -> cache is updated first and then the database in specified time intervals

### References
