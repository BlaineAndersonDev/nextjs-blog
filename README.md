## Useful NestJS Tips:
### **[Create Next.js App](https://nextjs.org/learn/basics/create-nextjs-app)**
* Automatically uses Hot Reloading (similiar to nodemon).
* Automatically creates routes using the 'tree' in pages (similar to react-router).
  * I.E. './pages/index.js' would be 'http://localhost:3000/'.
  * I.E. './pages/posts/first-post.js' would be 'http://localhost:3000/posts/first-post'.

### **[Navigate Between Pages](https://nextjs.org/learn/basics/navigate-between-pages)**
* Automatically uses:
  * Client-Side Navigation: 
    * Loads other components in the app using Javascript (faster than default navigation done by browser)
  * Code Splitting: 
    * Only loading the request pages assets and nothing more.
  * Prefetching (In Production):
    * The only exception to Code-Splitting being any 'Linked' components, which are preloaded to increase navigation speed.
  * Example Link Code, with className, target and rel:
    ```
    <Link href="/">
      <a className="foo" target="_blank" rel="noopener noreferrer">
        Hello World
      </a>
    </Link>
    ```

### **[Assests Metadata and CSS](https://nextjs.org/learn/basics/assets-metadata-css)**
* Assets: 
  * The './public' directory houses and serves:
    * Static Assets (like images).
    * 'robots.txt'
    * Google Site Verification
    * etc.
* Metadata (SEO):
  * Metadata is traditionally stored in `<head></head>`, however next.js has a special, built in component called `<Head></Head>` that can be imported and used on each component we build.
    ```
    import Head from 'next/head'
    <Head>
      <title>Create Next App</title>
      <link rel="icon" href="/favicon.ico" />
    </Head>
    ```
    * A [Custom Document](https://nextjs.org/docs/advanced-features/custom-document) can still be made if needed.
* Layout (A shared design element across all components/pages):
  * Housed in ./components, Layout can be imported into any or all pages and components to add a base level of styling.
  * I.E.
    ```
    import Head from 'next/head'
    import Link from 'next/link'
    import Layout from '../../components/layout'

    export default function FirstPost() {
      return (
        <Layout>
          <Head>
            <title>First Post</title>
            <link rel="icon" href="/favicon.ico" />
          </Head>
          <h1>First Post</h1>
          <h2>
            <Link href="/">
              <a>Back to home </a>
            </Link>
          </h2>
        </Layout>
      )
    }
    ```
* CSS
  * CSS Modules
    * CSS Modules automatically generate unique class names insuring that you will never have name collisions.
    * Next.js's Code Splitting also works with CSS Modules, allowing for even faster load times.
    * Best practices are to store ALL CSS Modules in the same directory as the files that import them, OR store them in one location elsewhere.
    * To make a CSS file a module, just specify it: `example.module.css`.
    * Example Layout.js:
      ```
      import styles from './layout.module.css'

      export default function Layout({ children }) {
        return <div className={styles.container}>{children}</div>
      }
      ```
    * Example Layout.module.css:
      ```
      .container {
        max-width: 36rem;
        padding: 0 1rem;
        margin: 3rem auto 6rem;
      }
      ```
    * 
  * Global CSS Styles:
    * Next.js supports a global file called `_app.js` to implement specific CSS styles on **every page**.
    * Create `_app.js` under ./pages with the following code:
      ```
      import '../styles/global.css'

      export default function App({ Component, pageProps }) {
        return <Component {...pageProps} />
      }
      ```
    * Create a directory called styles under root
    * Inside ./styles create `global.css`. Example base:
      ```
      html,
      body {
        padding: 0;
        margin: 0;
        font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Oxygen, Ubuntu,
          Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;
        line-height: 1.6;
        font-size: 18px;
      }

      * {
        box-sizing: border-box;
      }

      a {
        color: #0070f3;
        text-decoration: none;
      }

      a:hover {
        text-decoration: underline;
      }

      img {
        max-width: 100%;
        display: block;
      }
      ```
    * If the development server was running, restart it and the changes should now be live.

### **[Data Fetching](https://nextjs.org/learn/basics/data-fetching)**
* Blog posts in Markdown usually contain some information at the top called 'front-matter'. This information can be parsed using a package called 'gray-matter'
  * `npm install gray-matter`
* Pre-Rendering: 
  * `getStaticProps()` [Docs](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation)
  * Obtains information available in the filetree ahead of time and then pre-renders the page.
  * *Note - 'getStaticProps' runs on every request in development mode, but **only** at build time in production.*
* Server-Side Rendering:
  * `getServerSideProps()` [Docs](https://nextjs.org/docs/basic-features/data-fetching#getserversideprops-server-side-rendering)
  * Cannot be pre-rendered as its requests **must** be run on every request. (Not Recommened)
* Client-Side Rendering:
  * Statically Pre-Renders parts of the page that do not require external data.
  * On page load, fetches external data using Javascript to populate the remainging parts.
  * Great for User Dashboards, etc.
* SWR (stale-while-revalidate)
  * React Hooks for Remote Data Fetching [Docs](https://swr.now.sh/)

### **[Dynamic Routes](https://nextjs.org/learn/basics/dynamic-routes)**
* Creating a file in pages with [] means its a Next.js Dynamic Page. I.E. `[id].js`.
* 
* 

### **[API Routes](https://nextjs.org/learn/basics/api-routes)**
* 
* 
* 

### **[___](___)**
* 
* 
* 

### **[___](___)**
* 
* 
* 

### **[___](___)**
* 
* 
* 

### **[___](___)**
* 
* 
* 

### **[___](___)**
* 
* 
* 

### 
* `npm init next-app nextjs-blog`
* Start development server with `npm run dev`
* 
* 
* 
* 