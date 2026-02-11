# FastAPI

## Testing

AsyncClient while testing does not work as expected with FastAPI's lifespan (tear up, tear down logic).

## Sync Handlers

Sync function are run in a thread pool when a request arrives.
