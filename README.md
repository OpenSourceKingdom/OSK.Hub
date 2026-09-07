# OSK.Hub

Welcome to the Hub! This is meant to serve as the primary location for documentation on most systems developed in the OSK organization, primarily serving to describe and document the higher level, in-depth aspects of domains, architecture & design, etc. Documentation at the repository level will serve detailing more specific details that might be helpful to updating, maintaining, or specific use cases/setup details

Note: Information in this repository will be up to date with the latest APIs, SDKs, etc. as there is no current documentation history configured.

## 📖 Documentation Pages
For further information about these systems, please visit the **[Docs Page](https://opensourcekingdom.github.io/OSK.Hub/)** (or check the `/docs` folder).

### Documentation Updates

The current setup for the project is geared towards allowing sections, pages for each sections, and potential sub-pages if complexity requires. A sidenav yaml configuration is utilized in order to allow side bar navigation, and thus new pages should be added using a standard format to be displayed.

To add a new page and related information:
- Add any newly required sidebar options to `_data/sidenav.yml`
  - Data is expected in the following format:
  ```
  section-name:
    title: Required
    header: Optional
    pages:
      - page-id: id-of-page
        title: Optional
        url: /path/to/file
        subpages:
          - page-id: id-of-page
            title: Optional
            url: /path/to/file 
  ```
   - The section name is the root level id that a page will use to be associated with a specific section's side bar
   - Title is required for sections
   - Section Headers are optional, if not set then the default header will be 'Content'
   - Page id is required for pages
   - Page titles are optional, defaulting to the page-id, if not set
   - Page url is required and must be a valid path to a document
- Add a markdown file to /the/path/required and then provide the needed page header information for it to display as expected:
  ```
  layout: default
  section-id: highlights
  page-id: Cryptography
  ```
  - The section id MUST be one of the root property names in the sidenav data
  - page-id MUST be a page-id in the sidenav data
