<template>
  <section>

    <div class="vue">
      <ul class="tabs">
        <li v-on:click="change(1)" v-bind:class="{'active': isActive === 1}">テキスト変換</li>
        <li v-on:click="change(2)" v-bind:class="{'active': isActive === 2}">コマンドのみ吐き出し</li>
      </ul>

      <ul class="contents">
        <li v-if="isActive === 1">
          <div>
            <span>指定の文字列:</span>
            <p style="white-space: pre-line;">{{ specifiedString }}</p>
            <br>
            <textarea class="small" v-model="specifiedString" placeholder="add multiple lines"></textarea>

            <select v-model="selected">
              <option disabled value="">Please select one</option>
              <option>指定した文字列を含む行以外を削除</option>
              <option>B</option>
              <option>C</option>
            </select>
          </div>

          <div>
            <span>変換元テキスト:</span>
            <p style="white-space: pre-line;">{{ sourceText }}</p>
            <br>
            <textarea class="big"  v-model="sourceText" placeholder="add multiple lines"></textarea>
          </div>
        </li>
        <li v-else-if="isActive === 2">コンテンツ2コンテンツ2コンテンツ2コンテンツ2</li>
      </ul>
    </div>

  </section>
</template>

<script lang="ts">
export default {
  data () {
    return { isActive: 1, specifiedString: '', sourceText: '', selected: '' };
  },
  methods: {
    change(amount: number): void {
      this.isActive = amount;
    }
  }
};
</script>