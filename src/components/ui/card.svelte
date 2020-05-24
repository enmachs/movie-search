<!-- CARD COMPONENT FOR LIST OF MOVIES -->
<script>
    export let movie = {};
    const {
      url, medium_cover_image, slug,
      title_english, year
    } = movie;
</script>

<div class="column">
  <div class="card">
    <img class="card-img-top" src={medium_cover_image} alt={slug}>
    <div class="card-block">
      <h5 class="text-bold">{title_english}</h5>
    </div>
    <div class="card-footer">
      <span class="float-right">
        <a href={url} target="_blank">TYS page</a>
      </span>
      <span><i class=""></i>{year}</span>
    </div>
  </div>
</div>

<style>
  .column {
    float: left;
    width: 25%;
    padding: 10px 10px;
  }

  /* Responsive columns */
  @media screen and (max-width: 600px) {
    .column {
      width: 100%;
      display: block;
      margin-bottom: 20px;
    }
  }
  .card {
    font-size: 1em;
    overflow: hidden;
    padding: 0;
    border: none;
    border-radius: .28571429rem;
    box-shadow: 0 1px 3px 0 #d4d4d5, 0 0 0 1px #d4d4d5;
  }

  .card-block {
    font-size: 1em;
    position: relative;
    margin: 0;
    padding: 1em;
    border: none;
    border-top: 1px solid rgba(34, 36, 38, .1);
    box-shadow: none;
  }

  .card-img-top {
    display: block;
    width: 100%;
    height: auto;
  }

  .text-bold {
    font-weight: 700;
  }

  .card-footer {
    font-size: 1em;
    position: static;
    top: 0;
    left: 0;
    max-width: 100%;
    padding: .75em 1em;
    color: rgba(0, 0, 0, .4);
    border-top: 1px solid rgba(0, 0, 0, .05) !important;
    background: #fff;
  }

  .float-right {
    float: right;
  }
</style>