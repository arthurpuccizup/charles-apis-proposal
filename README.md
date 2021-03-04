- See the "PATCH" method bellow the POST workspace, it's a proposal of perhaps allowing to create a workspace with all it's properties, but requiring only the name

- Use the same idea of the workspace creation to the circle creation, allowing to create a circle with all it's configuration or not, requiring only the name, excepts if is the API for crating with a file

- Does it makes sense to allow the exclusion of the required configuration of the workspace, such as matcher and butler?

- Open sea specific resources, removing it from circles listing and find by id

- Use components individually, asking helm templates for each one, this way the "module" idea will be removed, this is proposal in the "patch" resource of components,
if it's used in that way delete component it's needed

- Don't control users, only use a username, and all the user control stays at the IDM, and when creating a user group, only requires an username, 
and remove the user entity management from our domain

Some business rules:

- If exists specific resources for open sea, it's not possible to see it in the listing, the getById resources returns 404 when passing it id,
and the same for any other API that receives a circle id;

- All the exclusion, should be done in logical manner, and will have a history table with all the events for each entity;

- When deleting a workspace, do it asynchronously

- If not controlling users, the removal of an user from a workspace should use an internal id generated for each relation user - user group for security reasons

- Continuing the idea of not controlling users, there will exist a "root" user group, that will have all the root users, this group will come by default and contains the charlesadmin user,
and that group cannot be deleted, and the charlesadmin could not be disassociated from this group
  





- If user stays as the new idea, make some APIs for listing all groups of a user or disassociate a user from all groups that he is part of

- Deploy components using the name or the id?

- Is possible to make the rollback?

- Component removal from open sea?

- History APIs

