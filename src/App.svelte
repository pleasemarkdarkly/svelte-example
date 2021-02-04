<script lang="ts">
  import router from 'page';
  import Index from './routes/index.svelte';
  import Landing from './routes/landing.svelte';
  import Login from './routes/login.svelte';
  import Posts from './routes/posts.svelte';
  import Documents from './routes/documents.svelte';
  import Data from './routes/data-display.svelte';

  import About from './routes/about.svelte';
  import NotFound from './routes/notfound.svelte';

  let page: any;
  let params = {};
  let qs = {};

  router('/', () => (page = Index));
  router('/about', () => (page = About));
  router('/landing', () => (page = Landing));
  router('/documents', () => (page = Documents));
  router('/data', () => (page = Data));
  router('/login', () => (page = Login));
  router('/posts', () => (page = Posts));
  // router('/pdfs', () => (page = PDFS));
  router(
    '/404/:msg',
    (ctx: { params: {}; querystring: string }, next: any) => {
      params = ctx.params;
      next();
    },
    () => (page = NotFound),
  );
  router('/*', () => (page = NotFound));
  router.start();
</script>

<svelte:component this={page} {params} {qs} />
