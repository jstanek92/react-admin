



## Features

* Adapts to any backend (REST, GraphQL, SOAP, etc.)
* Powered by [material-ui](https://material-ui.com/), [redux](https://redux.js.org/), [redux-form](https://redux-form.com/7.3.0/), [redux-saga](https://redux-saga.js.org/), [react-router](https://reacttraining.com/react-router/), [recompose](https://github.com/acdlite/recompose), [reselect](https://github.com/reduxjs/reselect) and a few more
* Super-fast UI thanks to optimistic rendering (renders before the server returns)
* Undo updates and deletes for a few seconds
* Complete documentation
* Relationships (many to one, one to many)
* Data Validation
* Internationalization (i18n)
* Conditional formatting
* Themeable
* Supports any authentication provider (REST API, OAuth, Basic Auth, ...)
* Full-featured datagrid (sort, pagination, filters)
* Filter-as-you-type
* Supports any form layout (simple, tabbed, etc.)
* Custom actions
* Large library of components for various data types: boolean, number, rich text, etc.
* WYSIWYG editor
* Customize dashboard, menu, layout
* Super easy to extend and override (it's just React components)
* Highly customizable interface
* Can connect to multiple backends
* Can be included in another React app
* Inspired by the popular [ng-admin](https://github.com/marmelab/ng-admin) library (also by marmelab)



## Installation

React-admin is available from npm. You can install it (and its required dependencies)
using:

```sh
npm install react-admin

#or
yarn add react-admin
```

## At a Glance

```jsx
// in app.js
import React from 'react';
import { render } from 'react-dom';
import { Admin, Resource } from 'react-admin';
import restProvider from 'ra-data-simple-rest';

import { PostList, PostEdit, PostCreate, PostIcon } from './posts';

render(
    <Admin dataProvider={restProvider('http://localhost:3000')}>
        <Resource name="posts" list={PostList} edit={PostEdit} create={PostCreate} icon={PostIcon}/>
    </Admin>,
    document.getElementById('root')
);
```

The `<Resource>` component is a configuration component that allows to define sub components for each of the admin view: `list`, `edit`, and `create`. These components use Material UI and custom components from react-admin:

```jsx
// in posts.js
import React from 'react';
import { List, Datagrid, Edit, Create, SimpleForm, DateField, TextField, EditButton, TextInput, DateInput } from 'react-admin';
import BookIcon from '@material-ui/core/svg-icons/action/book';
export const PostIcon = BookIcon;

export const PostList = (props) => (
    <List {...props}>
        <Datagrid>
            <TextField source="id" />
            <TextField source="title" />
            <DateField source="published_at" />
            <TextField source="average_note" />
            <TextField source="views" />
            <EditButton basePath="/posts" />
        </Datagrid>
    </List>
);

const PostTitle = ({ record }) => {
    return <span>Post {record ? `"${record.title}"` : ''}</span>;
};

export const PostEdit = (props) => (
    <Edit title={<PostTitle />} {...props}>
        <SimpleForm>
            <TextInput disabled source="id" />
            <TextInput source="title" />
            <TextInput source="teaser" options={{ multiLine: true }} />
            <TextInput multiline source="body" />
            <DateInput label="Publication date" source="published_at" />
            <TextInput source="average_note" />
            <TextInput disabled label="Nb views" source="views" />
        </SimpleForm>
    </Edit>
);

export const PostCreate = (props) => (
    <Create title="Create a Post" {...props}>
        <SimpleForm>
            <TextInput source="title" />
            <TextInput source="teaser" options={{ multiLine: true }} />
            <TextInput multiline source="body" />
            <TextInput label="Publication date" source="published_at" />
            <TextInput source="average_note" />
        </SimpleForm>
    </Create>
);
```

## Does It Work With My API?

Yes.

React-admin uses an adapter approach, with a concept called *Data Providers*. Existing providers can be used as a blueprint to design your API, or you can write your own Data Provider to query an existing API. Writing a custom Data Provider is a matter of hours.

![Data Provider architecture](https://marmelab.com/react-admin/img/data-provider.png)

See the [Data Providers documentation](https://marmelab.com/react-admin/DataProviders.html) for details.

## Batteries Included But Removable

React-admin is designed as a library of loosely coupled React components built on top of [material-ui](https://material-ui.com/), in addition to controller functions implemented the Redux way. It is very easy to replace one part of react-admin with your own, e.g. to use a custom datagrid, GraphQL instead of REST, or bootstrap instead of Material Design.


# At the react-admin project root
make install

# or
yarn install

# Run the simple application
make run-simple
# Run the tutorial application
make build
make run-tutorial
# Run the demo application
make build
make run-demo
```

And then browse to the URL displayed in your console.


