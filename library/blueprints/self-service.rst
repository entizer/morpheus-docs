Self Service
============

The Self Service catalog (Tools > Self Service) is where administrators can create easily-deployable items for consumption by users operating under the "Service Catalog" Persona in |morpheus|. Catalog items can be fully-configured |morpheus| Instances or Blueprints, complete with user input through |morpheus| Option Types, automation Workflows, and more. The catalog items are presented in a simplified interface for ease of deployment without sacrificing configurability for administrators. All available catalog items are built in the Self Service area and users will see relevant items in their catalogs based on Role permissions.

.. NOTE:: For more on Personas and using the Service Catalog persona, see the Personas sections of our documentation.

Access is granted to the Self Service section through the Tools: Self Service Role permission. Users with Read rights can view the catalog while users with full rights can create and edit catalog items. Users without any rights to Self Service will not be able to access the page at all.

Additionally, a user's Role determines access to the standard and/or service catalog persona and which service catalog items are available for a user under the service catalog persona. See the Roles section of |morpheus| documentation for more information on administering Roles.

Viewing the Self Service Catalog
--------------------------------

The complete Self Service catalog can be viewed by clicking on Self Service from the Tools menu. The complete list of items available for the Self Service catalog are shown here but users working in the Service Catalog Persona will see only those allowed based on their user role. In addition to the name and type of each catalog item, we can also see a description and whether not the catalog item is featured or active. Featured items are given special visibility in the Service Catalog Persona and inactive items will not appear as provisioning options.

.. image:: /images/tools/self_service/catalogList.png

Building Catalog Instances
--------------------------

An Instance in |morpheus| is a set of one or more containers or virutal machines that correlate to a single, horizontally-scalable entity or service suite. From the Self Service section, we can pre-configure |morpheus| Instances and present them to users viewing the Service Catalog Persona for one-click deployment.

From the Catalog Items List Page (Tools > Self Service), click :guilabel:`ADD`. From the dropdown menu, select Instance. The modal window will appear to configure and add a new catalog Instance.

.. image:: /images/tools/self_service/createInstance.png

Configure the following:

- **NAME:** A friendly name for the catalog item in |morpheus|
- **DESCRIPTION:** An optional description identifying the catalog item
- **ENABLED:** When checked, this catalog item will be available for provisioning
- **FEATURED:** When checked, this catalog item will be given special visibility in the Service Catalog Persona view
- **VISIBILITY:** Set to private to keep the catalog item available only to users in the current Tenant. Master Tenant administrators may set catalog items to public to make them viewable and usable by Subtenant users
- **LOGO:** Select or upload a logo to be associated with this catalog item
- **CONFIG:** Enter, view, or edit Instance config here. Click :guilabel:`CONFIGURATION WIZARD` to build this catalog item through the |morpheus| Add Instance wizard
- **CONTENT:** Optionally include documentation content for this Catalog Item. Markdown-formatted text is accepted and displayed appropriately when the item is ordered from the Service Catalog. A new Catalog Item-type Wiki entry will also be added containing this information.
- **OPTION TYPES:** If desired, select Option Types to present users with mandatory or optional selections prior to provisioning

Once done, click :guilabel:`SAVE CHANGES`

.. TIP:: Building catalog items through the configuration wizard is similar to the typical provisioning process for Instances in |morpheus|. For more details on selections available in the configuration wizard, take a look at other sections of |morpheus| docs on provisioning Instances.

Building Catalog Blueprints
---------------------------

|morpheus| Blueprints allow for full multi-tier application deployment. In the Self Service catalog, user can create catalog items based on pre-existing App Blueprints. If new Blueprints need to be created for the Service Catalog, see other sections of |morpheus| docs on building App Blueprints of various supported types. Just like with catalog Instances, we can pre-configure Blueprints and present them to users viewing the Service Catalog Persona view for easy, one-click deployment.

From the Catalog Items List Page (Tools > Self Service), click :guilabel:`ADD`. From the dropdown menu, select Blueprint. The modal window will appear to configure and add a new catalog Blueprint.

Configure the following:

- **NAME:** A friendly name for the catalog item in |morpheus|
- **DESCRIPTION:** An optional description identifying the catalog item
- **ENABLED:** When checked, this catalog item will be available for provisioning
- **FEATURED:** When checked, this catalog item will be given special visibility in the Service Catalog Persona view
- **VISIBILITY:** Set to private to keep the catalog item available only to users in the current Tenant. Master Tenant administrators may set catalog items to public to make them viewable and usable by Subtenant users
- **LOGO:** Select or upload a logo to be associated with this catalog item
- **CONFIGURE:** Click :guilabel:`CONFIGURE` to use the familiar App provisioning wizard to tie Blueprint and App deployment configuration to the Catalog Item
- **APP SPEC:** Inject App spec here for any fields required to provision an App from your Blueprint. You may also inject any overrides to the existing Blueprint spec that are desired. App Spec configuration must be YAML, a simple example that names the App and sets the Group and Cloud is included below:

    .. code-block:: yaml

      #Example App Spec

      name: '<%= customOption.appName %>'
      group:
        name: Dev Group
      environment: Dev
      tiers:
        Web:
          instances:
            - instance:
                type: nginx
                cloud: Dev AWS
        App:
          instances:
            - instance:
                type: apache
                cloud: Dev AWS

- **CONTENT:** Optionally include documentation content for this Catalog Item. Markdown-formatted text is accepted and displayed appropriately when the item is ordered from the Service Catalog. A new Catalog Item-type Wiki entry will also be added containing this information.
- **OPTION TYPES:** If desired, select Option Types to present users with mandatory or optional selections prior to provisioning

  .. note:: App spec custom option variables should be single quoted in YAML: ``cloud: '<%= customOption.cloud %>'``

Once done, click :guilabel:`SAVE CHANGES`

Building Catalog Workflows
--------------------------

From the Catalog Items List Page (Tools > Self Service), click :guilabel:`ADD`. From the dropdown menu, select Workflow. The modal window will appear to configure and add a new catalog Workflow.

Configure the following:

- **NAME:** A friendly name for the catalog item in |morpheus|
- **DESCRIPTION:** An optional description identifying the catalog item
- **ENABLED:** When checked, this Workflow item will be available for selection in the Service Catalog
- **FEATURED:** When checked, this catalog item will be given special visibility in the Service Catalog Persona view
- **VISIBILITY:** Set to private to keep the catalog item available only to users in the current Tenant. Master Tenant administrators may set catalog items to public to make them viewable and usable by Subtenant users
- **LOGO:** Select or upload a logo to be associated with this catalog item
- **WORKFLOW:** Select an existing Workflow to be associated with this Catalog Item, new Workflows are created in Provisioning > Automation
- **CONTEXT TYPE:** Optionally restrict users to a specific target context, Instance, Server, or None
- **CONTENT:** Optionally include documentation content for this Catalog Item. Markdown-formatted text is accepted and displayed appropriately when the item is ordered from the Service Catalog. A new Catalog Item-type Wiki entry will also be added containing this information.

Once done, click :guilabel:`SAVE CHANGES`

Editing and Deleting from the Self Service Catalog
--------------------------------------------------

Once created, Service Catalog items can be edited or deleted from the Catalog Items list view (Tools > Self Service). Click the pencil icon in the relevant row to edit the Service Catalog item or the trash can icon to delete it. Alternatively, Service Catalog items can be made inactive to remove them as provisioning options rather than deleting them.
