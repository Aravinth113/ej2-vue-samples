<template>
  <div style="background-color:#404041;border-radius: 3px;">
    <img src="source/chart/images/male.png" style="width: 24px; height: 24px; padding: 2px">'
    <div
      style="color:white; font-family:Roboto; font-style: medium; fontp-size:14px; float: right;
         padding: 2px;line-height: 20px;text-align: center;padding-right: 6px;"
    >
      <span>{{data.point.y}}M </span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: {}
    };
  }
};
</script>