<script lang="ts">
  import { Snackbar, notifier, Button, Notifications, TextField } from "smelte";

  let showSnackbar = false;
  let showSnackbarTop = false;
  let showSnackbarBottomLeft = false;

  function notify() {
    notifier.notify(message);
  }

  let message = "";
</script>

<blockquote
  class="pl-8 mt-2 mb-10 border-l-8 border-primary-300 text-lg"
  cite="https://material.io/components/snackbars/#usage">
  <p>Snackbars inform users of a process that an app has performed or will perform. They appear temporarily, towards the bottom of the screen. They shouldn’t interrupt the user experience, and they don’t require user input to disappear.</p>

  <h6 class="mt-8">Frequency</h6>
  <p>Only one snackbar may be displayed at a time.</p>

  <h6 class="mt-8">Actions</h6>
  <p>A snackbar can contain a single action. Because they disappear automatically, the action shouldn’t be “Dismiss” or “Cancel.”</p>
</blockquote>


<Snackbar bind:value={showSnackbar}>
  <div>Have a nice day.</div>
  <div slot="action">
    <Button text on:click={() => (showSnackbar = false)}>Do something</Button>
  </div>
</Snackbar>

<Snackbar color="alert" top bind:value={showSnackbarTop}>
  <div>Have a nice day.</div>
</Snackbar>
<Snackbar
  noAction
  color="error"
  timeout={2000}
  left
  bind:value={showSnackbarBottomLeft}>
  <div>Something happened!</div>
  <div slot="action" />
</Snackbar>

<div class="py-2">
  <Button
    on:click={() => (showSnackbar = true)}
  >Show snackbar</Button>
</div>
<div class="py-2">
  <Button
    color="secondary"
    on:click={() => (showSnackbarTop = true)}
  >Show snackbar on top</Button>
</div>
<div class="py-2">
  <Button
    color="alert"
    on:click={() => (showSnackbarBottomLeft = true)}>Show snackbar on the bottom left</Button>
</div>

<p>Also Smelte comes with a simple notification queue implementation.</p>

<TextField bind:value={message} label="New message" />
<Button
  disabled={!message}
  on:click={notify}>Add message to queue</Button>

<Notifications />
