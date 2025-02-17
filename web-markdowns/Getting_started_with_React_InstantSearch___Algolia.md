Getting started with React InstantSearch | Algolia                      

[](/doc/)

Close

Guides

Learn how Algolia works and how you can use it to create search and discovery experiences.

[

Home



](/doc/)[

Getting started



](/doc/guides/getting-started/what-is-algolia/)[

Sending and managing data



](/doc/guides/sending-and-managing-data/prepare-your-data/)[

Managing results



](/doc/guides/managing-results/relevance-overview/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/android/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/angular/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/flutter/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/ios/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/js/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/react/)

[

Building Search UI



](/doc/guides/building-search-ui/what-is-instantsearch/vue/)

[

Sending events



](/doc/guides/sending-events/getting-started/)[

Search analytics



](/doc/guides/search-analytics/overview/)[

Personalization



](/doc/guides/personalization/ai-personalization/what-is-ai-personalization/)[

A/B testing



](/doc/guides/ab-testing/what-is-ab-testing/)[

Algolia Recommend



](/doc/guides/algolia-recommend/overview/)[

Algolia AI



](/doc/guides/algolia-ai/dynamic-synonym-suggestions/)[

Going to production



](/doc/guides/going-to-production/preparing-your-project/)[

Scaling



](/doc/guides/scaling/servers-clusters/)[

Security



](/doc/guides/security/api-keys/)[

Solutions



](/doc/guides/solutions/ecommerce/search/)

API clients

[

PHP



](/doc/api-client/getting-started/install/php/)[

Ruby



](/doc/api-client/getting-started/install/ruby/)[

JavaScript



](/doc/api-client/getting-started/install/javascript/)[

Python



](/doc/api-client/getting-started/install/python/)[

Swift



](/doc/api-client/getting-started/install/swift/)[

Kotlin



](/doc/api-client/getting-started/install/kotlin/)[

.NET



](/doc/api-client/getting-started/install/csharp/)[

Java



](/doc/api-client/getting-started/install/java/)[

Go



](/doc/api-client/getting-started/install/go/)[

Scala



](/doc/api-client/getting-started/install/scala/)

UI libraries

[

InstantSearch.js



](/doc/api-reference/widgets/js/)[

React InstantSearch



](/doc/api-reference/widgets/react/)[

Vue InstantSearch



](/doc/api-reference/widgets/vue/)[

Angular InstantSearch



](/doc/api-reference/widgets/angular/)[

InstantSearch iOS



](/doc/api-reference/widgets/ios/)[

InstantSearch Android



](/doc/api-reference/widgets/android/)[

Algolia for Flutter



](/doc/guides/building-search-ui/widgets/showcase/flutter/)

[

Autocomplete



](/doc/ui-libraries/autocomplete/introduction/what-is-autocomplete/)

API parameters

[

Index settings and search parameters



](/doc/api-reference/api-parameters/)

REST API

[

A full reference of API endpoints



](/doc/api-reference/rest-api/)

Crawler

[

Configuration API



](/doc/tools/crawler/apis/configuration/)

Integrations

Speed up your implementation with Algolia's integrations and tools.

Web frameworks

[

Rails



](/doc/framework-integration/rails/getting-started/setup/)[

Symfony



](/doc/framework-integration/symfony/getting-started/algolia-searchbundle/)[

Django



](/doc/framework-integration/django/setup/)[

Laravel



](/doc/framework-integration/laravel/getting-started/introduction-to-scout-extended/)

Tools

[

Crawler



](/doc/tools/crawler/getting-started/overview/)[

CLI



](/doc/tools/cli/get-started/overview/)

Platforms

[

Magento 2



](/doc/integration/magento-2/getting-started/quick-start/)[

Shopify



](/doc/integration/shopify/getting-started/quick-start/)[

commercetools



](/doc/integration/commercetools/getting-started/installation)[

BigCommerce



](/doc/integration/bigcommerce/get-started/installation)[

Salesforce Commerce Cloud B2C



](/doc/integration/salesforce-commerce-cloud-b2c/getting-started/introduction/)[

Netlify



](/doc/tools/crawler/netlify-plugin/quick-start/)[

Zendesk



](/doc/integration/zendesk/get-started/)

Guides / Building Search UI

Jul 10, 2024

Getting started with React InstantSearch
========================================

[Edit this guide](https://github.com/algolia/doc/edit/master/source/doc/guides/04-building-search-ui/02-getting-started/react.html.md.erb) [A Edit this guide](https://atwood-editor.algolia.com/?gh-paths=source/doc/guides/04-building-search-ui/02-getting-started/react.html.md.erb "Edit this guide")

**This is the React InstantSearch v7 documentation.** React InstantSearch v7 is the latest version of React InstantSearch and the stable version of React InstantSearch Hooks.  
  
If you were using React InstantSearch v6, you can [upgrade to v7](/doc/guides/building-search-ui/upgrade-guides/react/#migrate-from-react-instantsearch-v6-to-react-instantsearch-v7).  
  
If you were using React InstantSearch Hooks, you can still use the React InstantSearch v7 documentation, but you should check the [upgrade guide](/doc/guides/building-search-ui/upgrade-guides/react/#migrate-from-react-instantsearch-hooks-to-react-instantsearch-v7) for necessary changes.  
  
If you want to keep using React InstantSearch v6, you can find the [archived documentation](/doc/deprecated/instantsearch/react/v6/api-reference/instantsearch/).

##### On this page

*   [1\. Before you begin](/doc/guides/building-search-ui/getting-started/react/#before-you-begin)
*   [2\. Add InstantSearch to your app](/doc/guides/building-search-ui/getting-started/react/#add-instantsearch-to-your-app)
*   [3\. Add a search box](/doc/guides/building-search-ui/getting-started/react/#add-a-search-box)
*   [4\. Display hits](/doc/guides/building-search-ui/getting-started/react/#display-hits)
*   [5\. Highlight matches](/doc/guides/building-search-ui/getting-started/react/#highlight-matches)
*   [6\. Sending click and conversion events](/doc/guides/building-search-ui/getting-started/react/#sending-click-and-conversion-events)
*   [7\. Filter with a refinement list](/doc/guides/building-search-ui/getting-started/react/#filter-with-a-refinement-list)
*   [8\. Paginate your results](/doc/guides/building-search-ui/getting-started/react/#paginate-your-results)
*   [9\. Configure search parameters](/doc/guides/building-search-ui/getting-started/react/#configure-search-parameters)
*   [10\. Next steps](/doc/guides/building-search-ui/getting-started/react/#next-steps)

**React InstantSearch** is a [React](https://reactjs.org) library that lets you create an instant search results experience using Algolia’s search API.

This guide covers how to integrate InstantSearch in your React application:

*   Adding a search box to send textual queries
*   Displaying and highlighting hits
*   Filtering to narrow down the results set
*   Paginating results to navigate
*   Applying search parameters

Before you begin
----------------

**This guide assumes React knowledge and an existing app using React ≥ [16.8.0](https://reactjs.org/blog/2019/02/06/react-v16.8.0.html).** If you don’t already have a running React app, you can start with this [CodeSandbox React template](https://codesandbox.io/s/react-new).

Then, **install `algoliasearch` and `react-instantsearch`** following the [installation guide](/doc/guides/building-search-ui/installation/react/).

Add InstantSearch to your app
-----------------------------

The root component to start using React InstantSearch is the [`<InstantSearch>`](/doc/api-reference/widgets/instantsearch/react/) provider. This component connects your InstantSearch app to your Algolia application. It accepts a search client and the index to search into.

App.jsx

Copy

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    import algoliasearch from 'algoliasearch/lite';
    import { InstantSearch } from 'react-instantsearch';
    
    const searchClient = algoliasearch('YourApplicationID', 'YourSearchOnlyAPIKey');
    
    function App() {
      return (
        <InstantSearch searchClient={searchClient} indexName="instant_search">
          {/* ... */}
        </InstantSearch>
      );
    }
    

You can use any [Hook and widget](/doc/api-reference/widgets/react/) in [`<InstantSearch>`](/doc/api-reference/widgets/instantsearch/react/).

Add a search box
----------------

The main UI component of a search experience is a search box. It’s usually your users’ entry point to discover the content of the app.

React InstantSearch provides a [`<SearchBox>`](/doc/api-reference/widgets/search-box/react/) widget to display a search box connected to Algolia.

App.jsx

Copy

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    import algoliasearch from 'algoliasearch/lite';
    import { InstantSearch, SearchBox } from 'react-instantsearch';
    
    const searchClient = algoliasearch('YourApplicationID', 'YourSearchOnlyAPIKey');
    
    function App() {
      return (
        <InstantSearch searchClient={searchClient} indexName="instant_search">
          <SearchBox />
        </InstantSearch>
      );
    }
    

If you try typing in the search box, you won’t see any hits on the page yet. However, the component is connected to Algolia and is already sending queries: if you open the **Network** tabs in your browser’s developer tools, you can see network requests going out on every keystroke. InstantSearch adds the input value in the “query” [`uiState`](/doc/api-reference/widgets/ui-state/js/), which is then converted to search parameters and sent to Algolia.

Network tab for the query “iPhone”

You’ve got results coming from Algolia, you now need to display them.

Display hits
------------

When Algolia returns new results, you want to list them in the UI. You can use the [`<Hits>`](/doc/api-reference/widgets/hits/react/) widget.

App.jsx

Copy

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    21
    22
    23
    24
    import algoliasearch from 'algoliasearch/lite';
    import { InstantSearch, SearchBox, Hits } from 'react-instantsearch';
    
    const searchClient = algoliasearch('YourApplicationID', 'YourSearchOnlyAPIKey');
    
    function Hit({ hit }) {
      return (
        <article>
          <img src={hit.image} alt={hit.name} />
          <p>{hit.categories[0]}</p>
          <h1>{hit.name}</h1>
          <p>${hit.price}</p>
        </article>
      );
    }
    
    function App() {
      return (
        <InstantSearch searchClient={searchClient} indexName="instant_search">
          <SearchBox />
          <Hits hitComponent={Hit} />
        </InstantSearch>
      );
    }
    

Now, hits update whenever you type a character in the search box.

Hits without highlighting

You may notice that it’s hard to understand why a hit is ranked higher than others. To improve this experience, **you can highlight the parts of a result that matched the query.**

Highlight matches
-----------------

Algolia supports [highlighting](/doc/guides/getting-started/how-algolia-works/in-depth/features/#highlighting-and-snippeting) and returns the highlighted parts of a hit in the response. You can use the [`<Highlight>`](/doc/api-reference/widgets/highlight/react/) widget to highlight matches in each attribute.

App.jsx

Copy

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    21
    22
    23
    24
    25
    26
    27
    28
    29
    30
    31
    import algoliasearch from 'algoliasearch/lite';
    import {
      InstantSearch,
      SearchBox,
      Hits,
      Highlight,
    } from 'react-instantsearch';
    
    const searchClient = algoliasearch('YourApplicationID', 'YourSearchOnlyAPIKey');
    
    function Hit({ hit }) {
      return (
        <article>
          <img src={hit.image} alt={hit.name} />
          <p>{hit.categories[0]}</p>
          <h1>
            <Highlight attribute="name" hit={hit} />
          </h1>
          <p>${hit.price}</p>
        </article>
      );
    }
    
    function App() {
      return (
        <InstantSearch searchClient={searchClient} indexName="instant_search">
          <SearchBox />
          <Hits hitComponent={Hit} />
        </InstantSearch>
      );
    }
    

Now you can better understand why a hit ranks higher than others.

Hits with highlighting

Sending click and conversion events
-----------------------------------

To send [click and conversion events](/doc/guides/sending-events/getting-started/) when users interact with your search UI, set the [`insights`](/doc/api-reference/widgets/instantsearch/react/#widget-param-insights) option to `true`.

App.jsx

Copy

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    21
    22
    23
    24
    25
    26
    27
    28
    29
    30
    31
    import algoliasearch from 'algoliasearch/lite';
    import {
      InstantSearch,
      SearchBox,
      Hits,
      Highlight,
    } from 'react-instantsearch';
    
    const searchClient = algoliasearch('YourApplicationID', 'YourSearchOnlyAPIKey');
    
    function Hit({ hit }) {
      return (
        <article>
          <img src={hit.image} alt={hit.name} />
          <p>{hit.categories[0]}</p>
          <h1>
            <Highlight attribute="name" hit={hit} />
          </h1>
          <p>${hit.price}</p>
        </article>
      );
    }
    
    function App() {
      return (
        <InstantSearch searchClient={searchClient} indexName="instant_search" insights>
          <SearchBox />
          <Hits hitComponent={Hit} />
        </InstantSearch>
      );
    }
    

Filter with a refinement list
-----------------------------

A search box is a great way to refine a search experience, but sometimes you need to narrow down the results to find what you’re looking for in a specific category. You can use [`<RefinementList>`](/doc/api-reference/widgets/refinement-list/react/) to filter items based on their brand, size, color, etc.

App.jsx

Copy

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    21
    22
    import algoliasearch from 'algoliasearch/lite';
    import {
      InstantSearch,
      SearchBox,
      Hits,
      Highlight,
      RefinementList,
    } from 'react-instantsearch';
    
    const searchClient = algoliasearch('YourApplicationID', 'YourSearchOnlyAPIKey');
    
    // ...
    
    function App() {
      return (
        <InstantSearch searchClient={searchClient} indexName="instant_search" insights>
          <SearchBox />
          <RefinementList attribute="brand" />
          <Hits hitComponent={Hit} />
        </InstantSearch>
      );
    }
    

Refinement lists let you refine on multiple values. React InstantSearch provides more refinement widgets with specialized behaviors:

*   [`<Menu>`](/doc/api-reference/widgets/menu/react/) to refine on a single value per attribute
*   [`<HierarchicalMenu>`](/doc/api-reference/widgets/hierarchical-menu/react/) to filter down a hierarchy of categories
*   [`<ToggleRefinement>`](/doc/api-reference/widgets/toggle-refinement/react/) to filter on and off on a given attribute value

Once you start adding multiple refinement UI widgets, you can use [`<CurrentRefinements>`](/doc/api-reference/widgets/current-refinements/react/) to display all the active filters and let users remove them individually.

Paginate your results
---------------------

The app only shows 20 hits but Algolia returns more results.

Network tab showing the number of hits and the number of pages

You can use the [`<Pagination>`](/doc/api-reference/widgets/pagination/react/) widget to navigate through all the pages.

App.jsx

Copy

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    21
    22
    import algoliasearch from 'algoliasearch/lite';
    import {
      InstantSearch,
      SearchBox,
      Hits,
      Highlight,
      RefinementList,
      Pagination,
    } from 'react-instantsearch';
    
    // ...
    
    function App() {
      return (
        <InstantSearch searchClient={searchClient} indexName="instant_search" insights>
          <SearchBox />
          <RefinementList attribute="brand" />
          <Hits hitComponent={Hit} />
          <Pagination />
        </InstantSearch>
      );
    }
    

Configure search parameters
---------------------------

Algolia returns 20 hits by default, but you can override any [search parameters](/doc/api-reference/search-api-parameters/) with [`<Configure>`](/doc/api-reference/widgets/configure/react/). This widget doesn’t render anything, but still instructs InstantSearch to send custom search parameters to Algolia.

You can render the `<Configure>` widget in your app, specifying 40 hits per page.

App.jsx

Copy

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    21
    22
    23
    24
    import algoliasearch from 'algoliasearch/lite';
    import {
      InstantSearch,
      SearchBox,
      Hits,
      Highlight,
      RefinementList,
      Pagination,
      Configure,
    } from 'react-instantsearch';
    
    // ...
    
    function App() {
      return (
        <InstantSearch searchClient={searchClient} indexName="instant_search" insights>
          <Configure hitsPerPage={40} />
          <SearchBox />
          <RefinementList attribute="brand" />
          <Hits hitComponent={Hit} />
          <Pagination />
        </InstantSearch>
      );
    }
    

You can pass any [search parameters](/doc/api-reference/search-api-parameters/) to [`<Configure>`](/doc/api-reference/widgets/configure/react/), even reactive props coming from the React state but **you shouldn’t overuse [`<Configure>`](/doc/api-reference/widgets/configure/react/).** If you need to set a search parameter after a user interaction, you may want to use a [refinement widget](#filter-with-a-refinement-list).

Next steps
----------

You now have a good starting point to create an even more dynamic experience with React InstantSearch. Next up, you could improve this app by:

*   Loading hits without pagination using [`<InfiniteHits>`](/doc/api-reference/widgets/infinite-hits/react/).
*   Searching in multiple indices with [`<Index>`](/doc/api-reference/widgets/index-widget/react/).
*   Checking the [API reference](/doc/api-reference/widgets/react/) to discover more widgets and Hooks.
*   [Server-side rendering](/doc/guides/building-search-ui/going-further/server-side-rendering/react/) your application for increased performance.

[

Previous

What is React InstantSearch?



](/doc/guides/building-search-ui/what-is-instantsearch/react/ "What is React InstantSearch?")

[

Next

Installation

](/doc/guides/building-search-ui/installation/react/ "Installation")

[

Start building for free today

No credit card required







](https://dashboard.algolia.com/users/sign_up)

Did you find this page helpful?

Yes, I found this page helpful.

No, I didn't find this page helpful.

We appreciate your feedback! Please note that we can't respond.

If you have questions, please reach out to [the support team](https://www.algolia.com/support/?contact=).

Looks like there's an issue on our end. Please copy the message below and send it to [the support team](https://www.algolia.com/support/?contact=).

Submit

React InstantSearch v7

[

InstantSearch Android v3





](/doc/guides/building-search-ui/getting-started/android/)[

Angular InstantSearch v4





](/doc/guides/building-search-ui/getting-started/angular/)[

Algolia for Flutter v1





](/doc/guides/building-search-ui/getting-started/flutter/)[

InstantSearch iOS v7





](/doc/guides/building-search-ui/getting-started/ios/)[

InstantSearch.js v4





](/doc/guides/building-search-ui/getting-started/js/)[

React InstantSearch v7





](/doc/guides/building-search-ui/getting-started/react/)[

Vue InstantSearch v4





](/doc/guides/building-search-ui/getting-started/vue/)

### On this page

*   [Before you begin](#before-you-begin)
*   [Add InstantSearch to your app](#add-instantsearch-to-your-app)
*   [Add a search box](#add-a-search-box)
*   [Display hits](#display-hits)
*   [Highlight matches](#highlight-matches)
*   [Sending click and conversion events](#sending-click-and-conversion-events)
*   [Filter with a refinement list](#filter-with-a-refinement-list)
*   [Paginate your results](#paginate-your-results)
*   [Configure search parameters](#configure-search-parameters)
*   [Next steps](#next-steps)

[Need help?](https://www.algolia.com/support/)

React InstantSearch v7

[

InstantSearch Android v3





](/doc/guides/building-search-ui/getting-started/android/)[

Angular InstantSearch v4





](/doc/guides/building-search-ui/getting-started/angular/)[

Algolia for Flutter v1





](/doc/guides/building-search-ui/getting-started/flutter/)[

InstantSearch iOS v7





](/doc/guides/building-search-ui/getting-started/ios/)[

InstantSearch.js v4





](/doc/guides/building-search-ui/getting-started/js/)[

React InstantSearch v7





](/doc/guides/building-search-ui/getting-started/react/)[

Vue InstantSearch v4





](/doc/guides/building-search-ui/getting-started/vue/)