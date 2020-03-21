# 概要
ubuntuでMeCab+Juman辞書の構築

# 環境
- ubuntu 18.04
- Miniconda

# 確認
## mecab
```
echo 今日はいい天気です。| mecab
```
## python
```
import MeCab
mecab = MeCab.Tagger("-d /var/lib/mecab/dic/juman-utf8")
print(mecab.parse("今日はいい天気です。"))
```

### 解析結果
```
今日    名詞,時相名詞,*,*,今日,きょう,代表表記:今日/きょう カテゴリ:時間
は      助詞,副助詞,*,*,は,は,*
いい    動詞,*,子音動詞ワ行,基本連用形,いう,いい,代表表記:言う/いう 補文ト
天気    名詞,普通名詞,*,*,天気,てんき,代表表記:天気/てんき カテゴリ:抽象物
です    判定詞,*,判定詞,デス列基本形,だ,です,*
。      特殊,句点,*,*,。,。,*
EOS
```