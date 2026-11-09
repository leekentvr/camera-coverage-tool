# カメラ視野チェッカー / Camera coverage checker

**日本語** · [English](#english)

平面図の上にカメラをドラッグして配置し、**各カメラに何が映るか、どこが重複し、どこが見えないか**を確認するための小さなブラウザツールです。リフレッシュスペース（3階）の検討用に作りました。

- インストール不要：`index.html` をブラウザで開くだけ（ダブルクリック）。
- 通信は一切ありません。画像もデータも外部に送りません。
- 画面右上の **日本語 / English** で表示言語を切り替えられます（初期表示は日本語）。

## 使い方

1. 上部の **「カメラを平面図へドラッグ」** タイルを、右側の平面図にドラッグして配置します（クリックでも追加できます）。
2. 平面図の番号の丸をドラッグして移動、白いリングをドラッグして向きを変えます。
3. 左の大きな映像で、選択中のカメラに何が映るかを確認します。壁・テーブル・ブースは実体として描かれ、後ろにあるものを隠します。
4. 映像の下で、取付高さ・向き・下向き角・ズームを調整します。
5. 平面図の **P ピン** をドラッグすると、その場所に座った人／立った人がどのカメラに、何ピクセルの大きさで映るかを確認できます。
6. 平面図の上の「視野を見る高さ」で、床面・座位の胸・立位の胸のどの高さで視野を見るかを切り替えます。
7. **画像を保存** で平面図を PNG に、**位置をコピー** でカメラ位置を文字として保存できます。

統計（1台で見える／2台以上＝重複／見えない／廊下が映る）は平面図の下に1行で表示されます。

## 何をモデル化しているか

- **レンズ**：Logitech C922。メーカー公称は対角78°・水平70.42°・垂直43.3°で、1920×1080 の映像として計算しています。
- **壁・柱・家具**：すべて立体として扱い、視界をさえぎります（オプションで切り替え可能）。壁のない北側は「廊下に開放」として表示し、廊下が映る面積を別に集計します。
- **人**：座位・立位とも胸の高さで判定します。

## 前提と限界

- 縮尺は図面上の柱間隔（6.0m）から算出しています。実際の部屋で5通り〜6通りの柱芯間をメジャーで測って確認してください。
- 壁・テーブル・ブースの位置は図面から読み取った値で、誤差は約±0.2mです。カメラの高さと壁の高さ（2.7m）は図面に無いため仮定です。
- レンズは歪みのない理想的なピンホールとして扱っています。実機での画角の実測はまだ行っていません。
- ズームはソフトウェアズームで、メーカーは範囲を公開していません。

## 部屋を変えるには

`index.html` の先頭付近にある `ROOM`・`WALLS`・`FURN`（単位はmm、原点は5/C柱の中心）を編集します。ほかのファイルはありません。

## ライセンス

未設定です。

---

## English

A small browser tool for dragging cameras onto a floor plan and checking **what each camera sees, where cameras overlap, and what nobody sees**. Built for planning the 3F Refresh Space.

- No install: open `index.html` in a browser (double-click).
- It makes no network requests. Nothing is uploaded.
- Use the **日本語 / English** toggle at the top right (Japanese is the default).

### How to use

1. Drag the **“Drag a camera onto the plan”** tile onto the floor plan on the right (or click it to add one).
2. Drag a numbered dot on the plan to move a camera, and drag the white ring to turn it.
3. The large picture on the left shows what the selected camera sees. Walls, tables and booths are solid and hide whatever is behind them.
4. Under the picture, adjust mounting height, direction, tilt down and zoom.
5. Drag the **P pin** on the plan to see whether a seated or standing person at that spot is in view of each camera, and how many pixels tall they appear.
6. Above the plan, choose the height coverage is shown at: floor, seated chest or standing chest.
7. **Save picture** saves the plan as a PNG; **Copy positions** copies the camera positions as text.

The statistics (seen by one camera, two or more = overlap, not seen, corridor in view) sit on a single row under the plan.

### What it models

- **Lens:** Logitech C922. Logitech lists 78° diagonal, 70.42° wide and 43.3° tall; the tool uses that for a 1920×1080 picture.
- **Walls, columns and furniture:** all solid, and they block the view (can be switched off in Options). The north side has no wall for most of its length; it is drawn as open to the corridor, and the corridor area a camera can see is counted separately.
- **People:** judged at chest height, seated or standing.

### Assumptions and limits

- The scale comes from the drawing, where the columns are 6.0 m apart. Tape one bay, column centre to column centre, to confirm.
- Walls, tables and booths are read off the drawing to about ±0.2 m. Camera height and wall height (2.7 m) are assumptions, since a floor plan has no heights.
- The lens is treated as a perfect pinhole (no distortion), and the field of view has not yet been measured on a real unit.
- Zoom is software zoom; Logitech does not publish its range.

### Changing the room

Edit `ROOM`, `WALLS` and `FURN` near the top of the script in `index.html` (millimetres; origin = centre of the 5/C column). There are no other files.

### Licence

None chosen yet.
