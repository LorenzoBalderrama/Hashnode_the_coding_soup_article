# Building Your Professional Presence: A Step-by-Step Guide to Creating a Stunning Portfolio with Next.js

In the world of web development, a portfolio website is an essential tool for showcasing your skills, projects, and expertise. Not only does it help you establish your online presence, but it also serves as a platform to attract potential clients and employers. In this article, we'll explore how to create a portfolio using Next.js, a popular framework for building server-side rendered React applications.

**Step 1: Set up a new Next.js project**

To get started, you need to set up a new Next.js project. You can do this by running the following command in your terminal or command prompt:

```javascript
npx create-next-app my-portfolio
```

This command creates a new Next.js project in a folder named `my-portfolio`. Once the installation is complete, navigate to the new project directory by running the following command:

```javascript
cd my-portfolio
```

**Step 2: Create the layout**

The first thing you need to do is create the layout for your portfolio website. This typically includes a header, a main content area, and a footer. In Next.js, you can use the `Layout` component to create a consistent layout across all pages of your website. Here's an example:

```javascript
import Head from 'next/head';
import Header from './Header';
import Footer from './Footer';

function Layout({ children, title = 'My Portfolio' }) {
  return (
    <div className="container">
      <Head>
        <title>{title}</title>
      </Head>
      <Header />
      <main>{children}</main>
      <Footer />
    </div>
  );
}

export default Layout;
```

This code creates a `Layout` component that includes a `Head` component for setting the title of the page, a `Header` component, a `main` element for the main content area, and a `Footer` component.

**Step 3: Create the pages**

Once you have the layout in place, you can start creating the pages for your portfolio website. You can create a new page by creating a new file in the `pages` directory. For example, to create a page named `About`, you can create a new file named `about.js` in the `pages` directory. Here's an example:

```javascript
import Layout from '../components/Layout';

function AboutPage() {
  return (
    <Layout title="About">
      <h1>About Me</h1>
      <p>I'm a web developer who loves building web applications.</p>
    </Layout>
  );
}

export default AboutPage;
```

This code creates an `AboutPage` component that uses the `Layout` component to create a consistent layout. The `title` prop is used to set the title of the page, and the content of the page is included inside the `main` element.

**Step 4: Style the website**

To make your portfolio website more visually appealing, you'll need to style it. Next.js supports CSS modules, which allow you to write modular, reusable CSS code. Here's an example of how to use CSS modules in Next.js:

```javascript
.container {
  max-width: 960px;
  margin: 0 auto;
  padding: 0 20px;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
  border-bottom: 1px solid #eaeaea;
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

nav ul {
  display: flex;
  justify-content: flex-end;
  margin: 0;
  padding: 0;
  list-style: none;
}

nav
```

**Step 4: Style the website (continued)**

```javascript
nav li {
  margin-left: 1rem;
}

nav a {
  font-size: 1.2rem;
  color: #333;
  text-decoration: none;
  transition: color 0.3s ease;
}

nav a:hover {
  color: #0070f3;
}

main {
  padding: 2rem 0;
}

footer {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100px;
  border-top: 1px solid #eaeaea;
}
```

This CSS code defines styles for the `Layout` component and its child elements. The `container` class sets the maximum width of the content area to 960px and centers it horizontally. The `header` and `footer` classes define styles for the header and footer sections of the layout, respectively. The `nav` class styles the navigation menu, and the `main` class styles the main content area.

**Step 5: Add content to the pages**

With the layout and styles in place, you can start adding content to the pages of your portfolio website. This typically includes information about yourself, your skills, your projects, and your contact information. Here's an example of how to create a page that lists your skills:

```javascript
import Layout from '../components/Layout';

function SkillsPage() {
  return (
    <Layout title="Skills">
      <h1>Skills</h1>
      <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>JavaScript</li>
        <li>React</li>
        <li>Node.js</li>
      </ul>
    </Layout>
  );
}

export default SkillsPage;
```

This code creates a `SkillsPage` component that uses the `Layout` component to create a consistent layout. The content of the page includes a heading and an unordered list of skills.

**Step 6: Deploy your portfolio website**

Once you've created your portfolio website, you need to deploy it so that others can access it. There are many ways to deploy a Next.js website, but one common approach is to use a hosting service such as Vercel or Heroku.

To deploy your portfolio website to Vercel, follow these steps:

1. Sign up for a Vercel account at [**https://vercel.com/**](https://vercel.com/).
    
2. Connect your portfolio website to Vercel by importing it from GitHub or GitLab.
    
3. Configure your deployment settings, such as the environment variables and the build command.
    
4. Deploy your website to the Vercel platform.
    

Once your website is deployed, you can access it using the URL provided by Vercel.

**Conclusion**

Creating a portfolio using Next.js can be a rewarding and enjoyable experience. By following the steps outlined in this article, you can create a professional-looking portfolio website that showcases your skills, projects, and expertise. Remember to keep your website up to date by adding new content and updating your projects as you complete them. With a little effort and creativity, you can create a portfolio that sets you apart from the competition and helps you achieve your career goals.

Follow me @the\_coding\_soup