## 今日やったこと
1. リーダブルコード10p読んだ：0.5h
2. Exercism(Squeaky Clean)を解いた:2h  


## 学び  
1. Matcherクラスを用いた文字列操作の実装を行った。
   - appendReplacement
     - パターンマッチした文字列を置換することのできるメソッド
     - パターンマッチ以前の文字列も保持することができる
   - appendTail
     - パターンマッチ以降の文字列をコピーして追加することのできるメソッド
   - 実装コード
   ```
   import java.util.Map;
    import java.util.regex.*;

    class SqueakyClean {
        static String clean(String identifier) {
            Matcher pattern = Pattern.compile("-([a-zA-Z])").matcher(identifier);
            StringBuffer cleaned_identifier = new StringBuffer();
            Map<String,String> leetSpeakWords = Map.of(
                "4","a",
                "3","e",
                "0","o",
                "1","l",
                "7","t"
                );
                
                while(pattern.find()){
                    pattern.appendReplacement(cleaned_identifier, pattern.group(1).toUpperCase());
                }
                pattern.appendTail(cleaned_identifier);
                
                String plainedIdentifier = leetSpeakToText(cleaned_identifier.toString(),leetSpeakWords);        
            return plainedIdentifier.replace(" ", "_").replaceAll("[^a-zA-Z0-9_]","");
        }

        private static String leetSpeakToText(String leetSpeakString, Map<String,String> map){

            for(Map.Entry<String,String> entry : map.entrySet()){
                leetSpeakString = leetSpeakString.replace(entry.getKey(), entry.getValue());
            }
            return leetSpeakString;
        }
    }
   ```
   - 学び
     - 文字列置換パターンが決まっているものについてはMatcherクラスが効果的だと感じた。
   - 参考サイト
     - https://docs.oracle.com/javase/jp/8/docs/api/java/util/regex/Matcher.html



2. Mapの拡張for文ループの実装について
   - すぐに思い出せなかったのでコードスニペットを残しておく
   ```
   for(Map.Entry<String,String> entry : map.entrySet()){
      leetSpeakString = leetSpeakString.replace(entry.getKey(), entry.getValue());
    }
   ```
 
## 明日のTodo
1. Exercism(Squeaky Clean)のリファクタリング
2. リーダブルコードを10p読む

## タグ
#Java #Matcher　#Exercism #Map