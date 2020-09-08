# cli vue
https://cli.vuejs.org/

# 前提
- node入っているか確認
```
sora-hashimoto@FVFZ32ZAL414 ~ % node -v
v12.18.0
```

# 実行
npm install -g @vue/cli

```
sora-hashimoto@FVFZ32ZAL414 ~ % vue -V   
@vue/cli 4.5.4
```

# vueのプロジェクト作成
`vue create vue-learn`

# ローカルのソースコードビルドして環境作成
`npm run serve`

# vueter
syntaxチェック的なやつをvscでインストール

# SFC
single file component

# vue3の話
typeScriptのサポート入ったから
jsx tsx辺がいい感じに使える

# requiredを渡さないとconsloeにエラー出る
``` 
vue.runtime.esm.js?2b0e:619 [Vue warn]: Missing required prop: "message"

found in

---> <Sample> at src/components/Sample.vue
       <App> at src/App.vue
         <Root>
warn @ vue.runtime.esm.js?2b0e:619
```
# vueはdivで囲わないと<p>は二つかけない
- templateの直近の子要素は一つだけにしないといけないという制約から


# 変数展開
- {{}}で変数展開
  - 基本こっち
- <p v-html="message"></p>
  - エスケープされない
  - リッチエディターとかの場合は使う

# propsはコンストラクタ引数みたいなもの

# dataはメンバ変数みたいなもの

# :number="number"
- :をつけることによって""の中をjsとして解釈する

# jsでオブジェクトとは{}

# 配列をコンポーネントとして表示したい時 keyが必須
```
v-for="item in items"
      :key="item.id"
      :message="item.message"
      :number="item.number"
```

# arrayのfilter
引数はコールバック関数になる。何を返すべきかはboolean
- trueだったら新しい配列含む
- falseだったら含まない

# computed
参照している変数が変わったら再演算された結果がでる

# 成果物
https://github.com/paop-13/vue-learn
