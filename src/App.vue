<script>
import { ref, reactive } from 'vue';
export default {
  setup() {
    const vocabularies = reactive([
      { en: 'provision', vn: 'nguồn dự trữ' },
      { en: 'costly', vn: 'tốn kém' },
      { en: 'obtain', vn: 'thu được' },
      { en: 'opportunity', vn: 'cơ hội, thời cơ' },
      // {en: "scare", vn: },
      { en: 'state benefits', vn: 'Những lợi ích quốc gia' },
      { en: 'income', vn: 'thu nhập' },
      { en: 'starve', vn: 'chết đói' },
      { en: 'curtail', vn: 'lấy đi' },
      { en: 'impact', vn: 'ảnh hưởng' },
      { en: 'certainly', vn: 'dĩ nhiên, tất nhiên' },
      { en: 'obesity', vn: 'béo phì' },
      { en: 'heart disease', vn: 'bệnh tim' },
      { en: 'diabetes', vn: 'bệnh tiểu đường' },
      { en: 'identity', vn: 'bản sắc' },
      { en: 'preparing skins', vn: 'thuộc da' },
      { en: 'disappear', vn: 'biến mất' },
      { en: 'incidence', vn: 'tì lệ mắc bệnh' },
      { en: 'depression', vn: 'trầm cảm' },
      { en: 'facilitate', vn: 'tạo điều kiện thuận lợi' },
      { en: 'controlling idea', vn: 'ý chủ đạo' },
      { en: 'digress', vn: 'lạc đề' },
      { en: 'incident', vn: 'sự cố' },
      { en: 'unusual', vn: 'bất thường' },
      { en: 'going off', vn: 'đi tiền trạm' },
      { en: 'seal', vn: 'con hải cẩu' },
      { en: 'canary in the mine', vn: 'điển tích con chim hoàng yến trong mỏ' },
      { en: 'insulating', vn: 'cách nhiệt' },
      { en: 'drip', vn: 'nhỏ giọt' },
      { en: 'refreeze', vn: 'đóng băng lại' },
      { en: 'permafrost', vn: 'băng vĩnh cữu' },
      { en: 'melt', vn: 'tan ra' },
      { en: 'knock-on', vn: 'ảnh hưởng dây chuyền' },
      { en: 'virtually', vn: 'hầu như' },
      { en: 'precipitation', vn: 'lượng mưa' },
      { en: 'increased', vn: 'tăng lên' },
      { en: 'sea level', vn: 'mực nước biển' },
      { en: 'keen to', vn: 'quan tâm tới' },
      { en: 'urgent', vn: 'cấp bách' },
      { en: 'precarious', vn: 'không ổn định' },
      { en: 'toughest', vn: 'khắc nghiệt' },
      { en: 'direct threat', vn: 'đe dọa trực tiếp' },
      { en: 'content', vn: 'hài lòng' },
      { en: 'hard-won', vn: 'khó khăn giành lấy' },
      { en: 'autonomy', vn: 'quyền tự trị' },
      { en: 'territory', vn: 'lãnh thổ' },
      { en: 'ancestral knowledge', vn: 'kiến thức của tổ tiên' },
      { en: 'terrain', vn: 'địa hình, địa thế' },
      { en: 'hardship facing', vn: 'khó khăn phải đối mặt' },
      { en: 'meagre', vn: 'nghèo nàn' },
      { en: 'picking', vn: 'lượm lặt' },
      { en: 'mammals', vn: 'động vật có vú' },
      { en: 'colonist', vn: 'người đi khai hoang' },
      { en: 'vanish', vn: 'biến mất' },
      { en: 'emerge', vn: 'xuất hiện' },
      { en: 'adapt', vn: 'thích nghi' },
      { en: 'pottery', vn: 'đồ gốm' },
      { en: 'ancestor', vn: 'ông bà, tổ tiên' },
      { en: 'descendant', vn: 'con cháu, hậu duệ' },
      { en: 'harsh', vn: 'khắc nghiệt' },
      { en: 'a handful', vn: 'một vài' },
      { en: 'indigenous', vn: 'người bản địa' },
      { en: 'abandoned', vn: 'bị bỏ rơi' },
      { en: 'nomadic ways', vn: 'lối sống du mục' },
      { en: 'isolate', vn: 'cô lập' },
      { en: 'relay on', vn: 'dựa vào' },
    ]);
    const currentWord = ref(null);
    const succeed = ref(localStorage.getItem('succeed') || 0);
    const failed = ref(localStorage.getItem('failed') || 0);

    function nextWord(scale) {
      const key = Math.floor(Math.random() * scale);
      currentWord.value = vocabularies[key];
    }

    function check(event) {
      event.target.value === currentWord.value.en
        ? succeed.value++
        : failed.value++;

      // Clear input's value after check.
      event.target.value = '';

      nextWord(vocabularies.length);
      localStorage.setItem('succeed', succeed.value);
      localStorage.setItem('failed', failed.value);
    }

    nextWord(vocabularies.length);

    return { currentWord, succeed, failed };
  },
};
</script>

<template>
  <h1>Vocabulary Checking</h1>
  {{ currentWord.vn }}: <input @keyup.enter="check" /> &nbsp;<span
    style="color: green"
    >{{ succeed }}</span
  >
  &nbsp;<span style="color: red">{{ failed }}</span>
</template>

<style>
#app {
  font-family: sans-serif;
}
</style>
