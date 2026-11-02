# 紅魔館図書館

本コレクションは、**メモリマネージャ**、**DOSエクステンダ**、および**DPMIホスト**の調査や実装に役立つ、DOS関連の歴史的な仕様書や参考資料をまとめたものです。

[`docs/dos/`](docs/dos/) ディレクトリに収められた文書は、386プロセッサ時代以降のDOS環境において重要な役割を果たしたレガシーインターフェースを扱っています。具体的には、EMS/XMSメモリサービス、VCPIやDPMIを通じたプロテクトモードへの移行、DMA仮想化（VDS）、サードパーティ製メモリマネージャ向けのAPI、そしてOpenDOS/DR-DOSにおけるプロテクトモードやマルチタスクに関する資料などが含まれます。

これらの資料は、当時の仕様書やマニュアルをアーカイブしたもの、あるいはそれらを忠実に書き起こした英語の文書で構成されています。PDF版とテキスト抽出版の両方が利用可能な場合は、PDF版を参照してください。`.txt` 形式や `.doc` 形式のファイルは、`grep` や `diff` といったツールを利用しやすくするために用意されています。

## 文書

| 文書 | 説明 |
| --- | --- |
| [DPMI 0.9](docs/dos/dpmispec09.txt) ([PDF](docs/dos/dpmispec09.pdf)) | DOS Protected Mode Interface 仕様バージョン 0.9。プロテクトモードのDOSプログラム向けに広く実装された Int 31h ホスト/クライアントAPI（ディスクリプタ、メモリ、割り込み、モード切り替えの各サービス）。 |
| [DPMI 1.0](docs/dos/dpmispec10.txt) ([PDF](docs/dos/dpmispec10.pdf)) | DPMI仕様バージョン 1.0（1991年3月）。共有メモリ、改善された例外処理、および1.0固有の呼び出しといったホストサービスで0.9を拡張する。商用ホストで完全実装されることは稀。 |
| [MS-DOS API Extensions for DPMI Hosts 0.04](docs/dos/msdos_dpmi_extensions_0.04.txt) ([PDF](docs/dos/msdos_dpmi_extensions_0.04.pdf)) | Microsoftのプレリリース0.04。DPMIホスト（特にWindowsエンハンストモード）が、プロテクトモードでのDOS/BIOS割り込みリフレクションと、小さな「MS-DOS」拡張エントリポイントをどう公開するかを述べる。 |
| [MS-DOS API Extensions for DPMI Hosts 0.02](docs/dos/msdos_dpmi_extensions_0.02.txt) | 同じ、プロテクトモード上のMS-DOS拡張に関する文書の、より古い1990年10月草案。 |
| [VCPI 1.0](docs/dos/vcpi.doc) | Virtual Control Program Interface。VCPI対応の386 EMS/メモリマネージャのもとでDOSエクステンダをプロテクトモードで動作させる（DPMI以前の業界インタフェース）。 |
| [XMS 2.0](docs/dos/xms20.txt) | eXtended Memory Specification 2.0。リアルモードDOS向けのHMA、A20制御、および拡張メモリブロックの割り当て・移動・ロック。 |
| [XMS 3.0](docs/dos/xms30.txt) | XMS 3.0。大きな空き容量/合計容量の問い合わせと関連する3.x機能を追加（最大約4GB級のマシン）。UMB呼び出しは引き続き任意。 |
| [XMS 3.5 / 3.51](docs/dos/xms35.txt) | 4GBを超えるスーパー拡張XMSに関する非公式メモ。一部の現代的なDOSメモリマネージャが用いる問い合わせ・割り当て・ロック・移動の拡張。 |
| [HIMEM notes](docs/dos/himem.txt) | `HIMEM.SYS` をXMS 2.0プロバイダとして、他の拡張メモリ利用者とどう関わるかを記したMicrosoftの短いメモ。 |
| [LIM EMS 3.2](docs/dos/limems32.txt) | Lotus/Intel/Microsoft Expanded Memory Specification 3.2。ページフレームとInt 67hによる、古典的なバンク切り替えEMS。 |
| [LIM EMS 4.0](docs/dos/limems40.txt) | EMS 4.0。容量の拡大と、より豊富なマッピングおよびOS機能。初期のEEMSの成果の多くを取り込んでいる。 |
| [EMS 4.0 vs EMS/EEMS 3.2](docs/dos/ems_vs_eems.txt) | Stephen Satchellによる、EMS 4.0とEMS 3.2およびAST/Quadram/Ashton-Tate EEMS 3.2との比較。 |
| [VDS](docs/dos/vds.txt) | Virtual DMA Services（Microsoft PW0519）。メモリマネージャやWindowsエンハンストモードのもとで物理ページを再マップする、DMAを使うドライバ向けAPI。 |
| [QPI](docs/dos/qpi.txt) | Ralf Brown / Dr. Dobb’s による、QEMM-386の未文書化QPIプログラミングインタフェース（メモリマップと関連マネージャサービス）の解説。 |
| [DPMS (OpenDOS)](docs/dos/dpms_opendos.pdf) | Caldera OpenDOS DPMS 1.0 APIガイド。ドライバやTSRを拡張メモリへ移し、小さなリアルモードスタブを残すためのDOS Protected Mode Services。 |
| [Multitasking API (OpenDOS)](docs/dos/multitask_opendos.pdf) | Caldera DR-DOS/OpenDOSマルチタスクAPIガイド。`EMM386 /MULTI` とTask Managerで使われる386マルチタスクコアのモジュール、および `X_*` / `Z_*` サービス。 |
| [PC DOS 7 Technical Update](docs/dos/pc_dos7_technical_update.pdf) | IBM GG24-4459。プログラマ向けのPC DOS 7技術アップデート。DPMSを扱う付録Eと、タスクスワップを扱う付録Fを含む。 |

## オープンソースプロジェクト

FreeDOS / SvarDOS および関連するコミュニティで使われている代表的なプロジェクトです。一次のソースリポジトリがある場合、リンクはそこを指します。

典型的な FreeDOS 構成は、**XMM**（HimemSX または XMGR、あるいは JemmEx 単体）→ 任意の **EMM/VCPI**（Jemm）→ 必要に応じた **DPMIホスト**（CWSDPMI、HDPMI、または DPMIONE）です。DOS/32A や HX などの DOSエクステンダは、独立したホスト TSR の代わりに独自の DPMI サーバを備えることがあります。

| プロジェクト | 役割 | リポジトリ |
| --- | --- | --- |
| [XMGR](https://gitlab.com/FreeDOS/drivers/xmgr) | 小型のXMS 3.0マネージャ（最大約4GB）。UMBPCI / Jemmと併用できる。 | [FreeDOS/drivers/xmgr](https://gitlab.com/FreeDOS/drivers/xmgr) |
| [Jemm](https://github.com/Baron-von-Riedesel/Jemm) | EMM / V86モニタ。EMS、UMB、VCPI、VDS（`Jemm386` はXMMが必要。`JemmEx` はXMMを内蔵）。 | [Baron-von-Riedesel/Jemm](https://github.com/Baron-von-Riedesel/Jemm) |
| [FreeDOS EMM386](https://github.com/FDOS/emm386) | JemmのFreeDOS向けパッケージ / ミラー（上流はBaron-von-Riedesel/Jemm）。 | [FDOS/emm386](https://github.com/FDOS/emm386) |
| [HimemSX](https://github.com/Baron-von-Riedesel/HimemSX) | XMSホスト（XMM）。XMS 3.5のスーパー拡張メモリ（4GB超、最大約1TB）に対応したHimemXのフォーク。Jemm386と併用されることが多い。 | [Baron-von-Riedesel/HimemSX](https://github.com/Baron-von-Riedesel/HimemSX) |
| [386MAX](https://github.com/sudleyplace/386MAX) | Qualitasの386メモリマネージャ（XMS/EMS/VCPI、GEMMIS）。DPMIONEの作者によるソース公開。 | [sudleyplace/386MAX](https://github.com/sudleyplace/386MAX) |
| [Open386MAX](https://github.com/geosone/Open386MAX) | 386MAXの開発が続いているフォーク。Linux上のオープンなツールチェーンによる再ビルド、現代環境向けの修正、QPI / XMS 3.5 / DPMI関連の作業。 | [geosone/Open386MAX](https://github.com/geosone/Open386MAX) |
| [CWSDPMI](https://github.com/jayschwa/cwsdpmi) | DJGPPで使われる古典的なフリーのDPMI 0.9ホスト（非公式のgitミラー）。 | [jayschwa/cwsdpmi](https://github.com/jayschwa/cwsdpmi) · [上流サイト](https://sandmann.dotster.com/cwsdpmi/) |
| [HDPMI](https://github.com/Baron-von-Riedesel/HX) | 多くの1.0機能を備えた独立したDPMI 0.9ホスト（`HDPMI16` / `HDPMI32`）。HXの一部。 | [Baron-von-Riedesel/HX](https://github.com/Baron-von-Riedesel/HX) |
| [DPMIONE](https://github.com/sudleyplace/DPMIONE) | 独立したDPMI **1.0** ホスト（386MAX系）。 | [sudleyplace/DPMIONE](https://github.com/sudleyplace/DPMIONE) |
| [DOS/32A](https://github.com/amindlost/dos32a) | DPMI 0.9サーバを内蔵したオープンソースのDOS/4GW互換エクステンダ。 | [amindlost/dos32a](https://github.com/amindlost/dos32a) |
| [HX DOS Extender](https://github.com/Baron-von-Riedesel/HX) | HDPMI上に構築された、DOS上でWin32 PEを実行するランタイム。 | [Baron-von-Riedesel/HX](https://github.com/Baron-von-Riedesel/HX) |