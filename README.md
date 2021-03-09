**Some changes**

- Now is possible to create a workspace, and circle with all its configurations, but the only required field is the name

- Open sea specific resources, removing it from circles listing and find by id

- Use components individually, asking helm templates for each one, this way the "module" idea will be removed, this is
  proposal in the "patch" resource of components, if it's used in that way delete component it's needed

- Don't control users, only use a username, and all the user control stays at the IDM, and when creating a user group,
  only requires a username, and remove the user entity management from our domain

- No more registry or git configuration, and CD configuration was changed to butler configuration

- No more hypothesis board

- Adding a resource to show the current status of the components in the cluster, by other means, show the current status
  of the pod

- Adding resource to show the currents virtual service and destination rules for each component registered at the
  workspace

**Some business rules:**

- It's not possible to see open sea in the listing, the getById resources returns 404 when passing it id, and the same
  for any other API that receives a circle id;

- All the exclusion, should be done in logical manner, and will have a history table with all the events for each
  entity;

- When deleting a workspace, do it asynchronously

- Will exist a "root" user group, that will have all the root users, this group will come by default and contains the
  charlesadmin user, and that group cannot be deleted, and the charlesadmin could not be disassociated from this group

- When a component is removed, is necessary to undeploy all it's release, from all circles and open sea

- Should make names of the resources unique keys for each workspace, in addition the workspace name should be unique as
  well

**Some questions**

- Deploy components using the name or the id?

- Is possible to make the rollback? (One way of doing that is using event sourcing schema)

- Component removal from open sea?

- Create a user id for each combination userGroup - user, or only use the username?

**Some notes**

- The circle history is just a model, for what the histories can be, they're grouped in the /histories and not
  individually for each resource, and they're basically a get with various query parameters that allow to filter the
  events

- Tg=here is also an idea to list the cluster events for that workspace, assuming, of course, that is one workspace to
  one namespace

- Not adding the system token functionality yet, since it's not done

- Not adding the webhooks functionality yet, since it may change