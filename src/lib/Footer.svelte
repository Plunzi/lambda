<footer id="primary-footer">
  <div class="footer">
    <div class="share-section">
      <div class="share">
        <p>Recommend</p>
      </div>
      <img class="social" src="/social/Instagram.png" alt="behance" />
      <img class="social" src="/social/Facebook.png" alt="" />
      <img class="social" src="/social/Youtube.png" alt="" />
      <img class="social" src="/social/TikTok.png" alt="" />
      <img class="social" src="/social/Twitter.png" alt="" />
      <img class="social" src="/social/Behance.png" alt="" />
    </div>
    <div style="margin-right: 1rem;">
      © 2023 Lambda Watches Ltd
    </div>
  </div>
</footer>

<style>
  :global(footer#primary-footer.hide) {
    transform: translateY(100%);
    transition: ease-in-out 1s;
  }

  img.social {
    width: 2.5rem;
    height: 2.5rem;
  }

  .footer {
    padding: .5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .share-section {
    align-items: center;
    display: flex;
    gap: 0.5rem;
    width: fit-content;
    background: #1a1a1a;
    padding: 0 0.5rem;
    border-radius: 8px;
  }

  footer {
    width: 100%;
    background: #000;
  }
</style>
