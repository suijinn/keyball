
# ビルドとProMicroへのflash手順

## Windows編

(*) QMK_MSYSのセットアップについては省略

1. 初回の準備
   1. QMK_MSYSで作業用フォルダに移動
   1. keyballのリポジトリクローン  
      $ git clone https://github.com/suijinn/keyball.git keyball
   1. qmk_firmwareのリポジトリクローン  
      対応しているバージョンに注意  
      $ git clone https://github.com/qmk/qmk_firmware.git --depth 1 --recurse-submodules --shallow-submodules -b 0.22.14 qmk
   1. keyball→qmk_firmwareへのシンボリックリンクを貼る  
      mklink /D %USERPROFILE%\qmk\keyboards\keyball %USERPROFILE%\keyball\qmk_firmware\keyboards\keyball
3. ビルド方法
   1. keyballリポジトリ以下を編集する。  
      keymapはkeyball44/my_keymap/以下を使う。
   1. ビルド&フラッシュ。qmk_firwmareのフォルダのトップで以下を実行。  
      $ qmk flash -kb keyball/keyball44 -km my_keymap

# やったことメモ

1. トラックボール加速機能実装  
   以下を参考にした。  
   https://x.com/mass_0X00/status/1824373363604853180
1. マウスキーを押すまでAutoMouseLayerに留まる  
   以下を参考にした。  
   https://github.com/negokaz/keyball/pull/2  
1. PERMISSIVE_HOLDを有効にした  
   押下時間に関係なく、押下中に他キー押下でHOLD判定になる。
1. QUICK_TAP設定をオフにした。  
   QUICK_TAP_TERMを0にすることでQUICK_TAP(連打)した際でもHOLDされるようにした。  
   https://golden-lucky.hatenablog.com/entry/2021/03/06/182958
1. マウスの加速設定をKB4でON/OFF変更できるようにした。

# 参考

* keyball qmkのReadme
  https://github.com/Yowkees/keyball/blob/main/qmk_firmware/keyboards/keyball/readme.md
* 環境構築
  https://note.com/yinouet1001/n/n54e6d3dc243a
