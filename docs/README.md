# Azure resources front-end

This plugin shows information about Azure resources related to your backstage entity

![backstage azure entity view](./img/entity-view.png)

## Getting started

[First install the backend plugin](https://github.com/ehrnst/backstage-azure-resources-backend). After that follow the below instructions.


```
# From your Backstage root directory
yarn add --cwd packages/app @vippsno/plugin-azure-resources
```

Add the following to `packages\app\src\components\catalog\EntityPage.tsx`

```TypeScript
import { AzureResourceEntityOverviewCard, EntityAzureSecurityOverviewCard } from '@vippsno/plugin-azure-resources';
```

```TypeScript
const azureResourceContent = (
  <Grid container spacing={3} alignItems="stretch">
    <Grid item md={6}>
      <AzureResourceEntityOverviewCard />
    </Grid>
    <Grid item md={6}>
      <EntityAzureSecurityOverviewCard />
    </Grid>
  </Grid>
);
```

```TypeScript
    <EntityLayout.Route path="/azure" title="Azure">
      {azureResourceContent}
    </EntityLayout.Route>
```

### Annotation

This plugin use a custom annotation from your entity. To use the plugin add the following annotation:

```YAML
annotations:
    azure.com/tag-selector: key/value
```

When doing Azure Resource Graph queries the plugin will use the tag key and its value to pull information.