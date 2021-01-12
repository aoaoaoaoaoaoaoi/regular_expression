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
            <br>
            <textarea class="small" v-model="specifiedString" placeholder="add multiple lines"></textarea>

            <select v-model="selected">
              <option disabled value="">Please select one</option>
              <option>指定した文字列を含まない行を削除</option>
              <option>半角スペースをタブ空白に変換</option>
              <option>C</option>
            </select>

            <button @click="execution(selected, specifiedString, sourceText)">実行</button>
          </div>

          <div>
            <span>変換元テキスト:</span>
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

    execution(selected: string, specifiedString: string, sourceText: string): void {
      if(selected == '指定した文字列を含まない行を削除'){
        if(specifiedString=='' || specifiedString.indexOf('\n') != -1){
          alert('指定の文字列に改行が含まれているため実行できません');
        }

        //行で分割
        const messages = sourceText.split('\n');
        const filterMessage = messages.filter(message => {
          return message.indexOf(specifiedString) != -1;
        });
        const result = filterMessage.join('\n');
        alert(result);
      }else if(selected == '半角スペースをタブ空白に変換'){
        const result = sourceText.replace(/ /g, '\t');
        alert(result);
      }
    }

  }
};
</script>