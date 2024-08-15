<script>
  export let sent;
</script>

<div class="container" class:sent>
  <div class="title">
    <img src="assets/icon-success-check.svg" alt="Message Sent icon">
    <b>Message Sent!</b>
  </div>
  <p>Thanks for completing the form. We’ll be in touch soon!</p>
</div>

<style>
  .container {
    background-color: var(--ntl-grey-900);
    padding: 2.4rem;
    border-radius: 1.2rem;
    display: grid;
    gap: .8rem;
    position: absolute;
    box-sizing: border-box;
    left: 50%;
    translate: -50% 0;
    top: -200px;
    width: 32.7rem;
    opacity: 0;
    transition: top 2s ease, opacity 2s ease;
  }
  
  .container.sent {
    top: 2.4rem;
    opacity: 1;
  }
  
  .title {
    display: flex;
    align-items: center;
    gap: .8rem;
    color: var(--ntl-white);
  }

  p {
    color: var(--pr-green-200);
  }

  @media (min-width: 768px) {
    .container {
      width: max-content;
    }
  }
</style>