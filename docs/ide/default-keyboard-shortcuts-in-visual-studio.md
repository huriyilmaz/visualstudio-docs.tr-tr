---
title: Klavye kısayolları
description: çeşitli komutlara ve windows 'a erişmenize olanak tanıyan Visual Studio varsayılan klavye kısayolları hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 09/23/2021
ms.topic: reference
helpviewer_keywords:
- shortcut keys [Visual Studio], keyboard binding schemes
- keyboard binding schemes [Visual Studio]
- Help [Visual Studio], shortcut keys
- keyboard shortcuts [Visual Studio], keyboard binding schemes
- keyboard shortcuts
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 75c7ddb84d561c123a7bb7bc1bc4a41df2a711b8
ms.sourcegitcommit: 65a1b6aae8387735f05a83b45e1a6865e9805e1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2021
ms.locfileid: "129339635"
---
# <a name="keyboard-shortcuts-in-visual-studio"></a>Visual Studio klavye kısayolları

uygun klavye kısayolunu seçerek Visual Studio içindeki çeşitli [komutlara](reference/visual-studio-commands.md) ve pencereler için erişebilirsiniz. Bu sayfa, Visual Studio yüklediğinizde seçmiş olabileceğiniz **genel** profil için varsayılan komut kısayollarını listeler. Seçtiğiniz profil ne olduğuna bakılmaksızın, **Seçenekler** iletişim kutusunu açıp **ortam** düğümünü genişleterek ve ardından **klavye**' yi seçerek bir komutun [kısayolunu belirleyebilirsiniz](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) . Ayrıca, verilen komutlardan herhangi birine farklı bir kısayol atayarak kısayollarınızı özelleştirebilirsiniz.

Yaygın klavye kısayollarının ve diğer üretkenlik bilgilerinin bir listesi için bkz.:

- [Klavye ipuçları](../ide/productivity-shortcuts.md)
- [Üretkenlik ipuçları](../ide/productivity-features.md)

Visual Studio erişilebilirlik hakkında daha fazla bilgi için bkz. [erişilebilirlik ipuçları ve püf noktaları](../ide/reference/accessibility-tips-and-tricks.md) ve [nasıl yapılır: klavyeyi özel olarak kullanma](../ide/reference/how-to-use-the-keyboard-exclusively.md).

## <a name="printable-shortcut-cheatsheet"></a>Yazdırılabilir kısayol yazdırılabilecek

[Visual Studio için yazdırılabilir klavye kısayol yazdırılabilecek](https://visualstudio.microsoft.com/keyboard-shortcuts.pdf)'i almak için tıklayın.

[:::image type="content" source="media/default-keyboard-shortcuts-in-visual-studio/visual-studio-keyboard-shortcut-cheatsheet.png" alt-text="Klavye kısayolları için yazdırılabilir yazdırılabilecek.":::](https://visualstudio.microsoft.com/keyboard-shortcuts.pdf)

<a name="popular"></a>
## <a name="popular-keyboard-shortcuts-for-visual-studio"></a>Visual Studio için popüler klavye kısayolları

Aksi belirtilmedikçe, bu bölümdeki tüm kısayollar Global olarak uygulanır. *Genel* bağlam, kısayolun Visual Studio tüm araç pencereleri için geçerli olduğu anlamına gelir.

> [!NOTE]
> **Seçenekler** iletişim kutusunu açıp **ortam** düğümünü genişleterek ve ardından **klavye**' yi seçerek herhangi bir komutun [kısayolunu arayabilirsiniz](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) .

- [Derleme](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build-popular-shortcuts)
- [Hata Ayıklama](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug-popular-shortcuts)
- [Düzenle](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit-popular-shortcuts)
- [Dosya](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file-popular-shortcuts)
- [Project](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project-popular-shortcuts)
- [Yeniden düzenleme](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor-popular-shortcuts)
- [Araçlar](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools-popular-shortcuts)
- [Görünüm](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view-popular-shortcuts)
- [Pencere](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window-popular-shortcuts)

#### <a name="build-popular-shortcuts"></a><a name="bkmk_build-popular-shortcuts"></a> Oluşturma: popüler kısayollar

|Komutlar|Klavye kısayolları |Komut KIMLIĞI|
|-|-|-|
|Çözüm oluştur|**Ctrl+Shift+B** | Build.BuildSolution |
|İptal|**Ctrl+Break tuşu** | Build.Cancel |
|Se|**Ctrl+F7** | Build.Compile |
|Çözümde Kod analizini Çalıştır|**Alt+F11**| Build.RunCodeAnalysisonSolution |

#### <a name="debug-popular-shortcuts"></a><a name="bkmk_debug-popular-shortcuts"></a> Hata Ayıkla: popüler kısayollar

|Komutlar|Klavye kısayolları [özel bağlamlar]|Komut KIMLIĞI|
|-|-|-|
|İşlevde kes|**Ctrl+B**| Debug.BreakatFunction |
|Tümünü kes|**Ctrl+Alt+Break tuşu**| Debug.BreakAll |
|Tüm kesme noktalarını Sil|**CTRL + SHIFT + F9**| Debug.DeleteAllBreakpoints |
|Özel durumlar|**Ctrl+Alt+E**| Debug.Exceptions |
|Hızlı Bakış|**Ctrl+Alt+Q**<br /><br />veya **SHIFT + F9**| Debug.QuickWatch |
|Yeniden başlat|**Ctrl+Shift+F5**| Debug.Restart |
|İmlece kadar Çalıştır|**Ctrl+F10**| Debug.RunToCursor |
|Sonraki ifadeyi ayarla|**Ctrl+Shift+F10**| Debug.SetNextStatement |
|Başlangıç|**F5**| Debug.Start |
|Hata ayıklama olmadan Başlat|**Ctrl+F5**| Debug.StartWithoutDebugging |
|Adımla|**F11**| Debug.StepInto |
|Dışarı adımla|**Shift+F11**| Debug.StepOut |
|Adımla|**F10**| Debug.StepOver |
|Hata ayıklamayı Durdur|**Shift+F5**| Debug.StopDebugging |
|Kesme noktasını aç|**F9**| Debug.ToggleBreakpoint |

#### <a name="edit-popular-shortcuts"></a><a name="bkmk_edit-popular-shortcuts"></a> Düzenle: popüler kısayollar

|Komutlar|Klavye kısayolları [özel bağlamlar]|Komut KIMLIĞI|
|-|-|-|
|Çizgiyi Böl|**Enter** [metin düzenleyicisi, Rapor Tasarımcısı, Windows Form Tasarımcısı]<br /><br />veya **SHIFT + enter** [metin düzenleyici]| Edit.BreakLine |
|Tanımları daralt|**Ctrl+M**, **Ctrl+O** [Metin Düzenleyici]| Edit.CollapseToDefinitions |
|Açıklama seçimi|**Ctrl+K**, **Ctrl+C** [Metin Düzenleyici]| Edit.CommentSelection |
|Tam sözcük|**Alt+Sağ Ok** [Metin Düzenleyici, İş Akışı Tasarımcısı]<br /><br />veya **Ctrl+Ara Çubuğu** [Metin Düzenleyici, İş Akışı Tasarımcısı]<br /><br />veya **Ctrl+K**, **W** [İş Akışı Tasarımcısı]<br /><br />veya **Ctrl+K, Ctrl+W** [İş Akışı Tasarımcısı]| Edit.CompleteWord |
|Kopyala|**Ctrl+C**<br /><br />veya **Ctrl+Insert tuşlarına basın**| Edit.Copy |
|Kes|**Ctrl+X**<br /><br />veya **Shift+Delete**| Edit.Cut |
|Sil|**Sil** [Takım Gezgini]<br /><br />veya **Shift+Delete** [Sıra Diyagramı, UML Etkinlik Diyagramı, Katman Diyagramı]<br /><br />veya **Ctrl+Delete** [Sınıf Diyagramı]| Edit.Delete |
|Bul|**Ctrl+F**| Edit.Find |
|Tüm başvuruları bulma|**Shift+F12**| Edit.FindAllReferences |
|Dosyalarda bulma|**Ctrl+Shift+F**| Edit.FindinFiles |
|Sonrakini bul|**F3**| Edit.FindNext |
|Sonraki seçileni bul|**Ctrl+F3**| Edit.FindNextSelected |
|Belgeyi biçimlendir|**Ctrl+K, Ctrl+D** [Metin Düzenleyici]| Edit.FormatDocument |
|Biçim seçimi|**Ctrl+K, Ctrl+F** [Metin Düzenleyici]| Edit.FormatSelection |
|Git|**Ctrl+G**| Edit.GoTo |
|Bildirime git|**Ctrl+F12**| Edit.GoToDeclaration |
|Tanıma git|**F12**| Edit.GoToDefinition |
|Birleşik giriş bulmak için gidin|**Ctrl+D**| Edit.GoToFindCombo |
|Sonraki konuma gidin|**F8**| Edit.GoToNextLocation |
|Kod parçacığı ekleme|**Ctrl+K**, **Ctrl+X**| Edit.InsertSnippet |
|Ekle sekmesi|**Sekme** [Rapor Tasarımcısı, Windows Forms Tasarımcısı, Metin Düzenleyici]| Edit.InsertTab |
|Satır kesme|**Ctrl+L** [Metin Düzenleyici]| Edit.LineCut |
|Satır aşağı genişletme sütunu|**Shift+Alt+Aşağı Ok** [Metin Düzenleyici]| Edit.LineDownExtendColumn |
|Yukarıda açık satır|**Ctrl+Enter** [Metin Düzenleyici]| Edit.LineOpenAbove |
|Üyeleri listele|**Ctrl+J** [Metin Düzenleyici, İş Akışı Tasarımcısı]<br /><br />veya **Ctrl+K, Ctrl+L** [İş Akışı Tasarımcısı]<br /><br />veya **Ctrl+K, L** [İş Akışı Tasarımcısı]| Edit.ListMembers |
| sayfasına gidin|**Ctrl+,**| Edit.NavigateTo |
|Dosya aç|**Ctrl+Shift+G**| Edit.OpenFile |
|Overtype modu|**Ekle** [Metin Düzenleyici]| Edit.OvertypeMode |
|Parametre bilgileri|**Ctrl+Shift+Ara Çubuğu** [Metin Düzenleyici, İş Akışı Tasarımcısı]<br /><br />veya **Ctrl+K, Ctrl+P** [İş Akışı Tasarımcısı]<br /><br />veya **Ctrl+K, P** [İş Akışı Tasarımcısı]| Edit.ParameterInfo |
|Yapıştır|**Ctrl+V**<br /><br />veya **Shift+Insert**| Edit.Paste |
|Tanıma göz atma|**Alt+F12** [Metin Düzenleyici]| Edit.PeekDefinition |
|Yinele|**Ctrl+Y**<br /><br />veya **Shift+Alt+Geri Al**<br /><br />veya **Ctrl+Shift+Z**| Edit.Redo |
|Değiştir|**Ctrl+H**| Edit.Replace |
|Tümünü seç|**Ctrl+A**| Edit.SelectAll |
|Geçerli sözcüğü seçme|**Ctrl+W** [Metin Düzenleyici]| Edit.SelectCurrentWord |
|Seçim iptali|**Esc** [Metin Düzenleyici, Rapor Tasarımcısı, Ayarlar Tasarımcısı, Windows Forms Tasarımcısı, Yönetilen Kaynaklar Düzenleyicisi]| Edit.SelectionCancel |
|Çevrele|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Sekme sol|**Shift+Sekme** [Metin Düzenleyici, Rapor Tasarımcısı, Windows Forms Düzenleyicisi]| Edit.TabLeft |
|Tüm altı çizili düğmeyi değiştir|**Ctrl+M, Ctrl+L** [Metin Düzenleyici]| Edit.ToggleAllOutlining |
|Yer işaretini değiştir|**Ctrl+K, Ctrl+K** [Metin Düzenleyici]| Edit.ToggleBookmark |
|Tamamlama modunu değiştir|**Ctrl+Alt+Ara Çubuğu** [Metin Düzenleyici]| Edit.ToggleCompletionMode |
|Altı çizili genişletmeyi değiştir|**Ctrl+M, Ctrl+M** [Metin Düzenleyici]| Edit.ToggleOutliningExpansion |
|Uncomment selection|**Ctrl+K, Ctrl+U** [Metin Düzenleyici]| Edit.UncommentSelection |
|Geri Al|**Ctrl+Z**<br /><br />veya **Alt+Geri Al**| Edit.Undo |
|Sona kadar sözcük silme|**Ctrl+Delete** [Metin Düzenleyici]| Edit.WordDeleteToEnd |
|Başlamak için sözcük silme|**Ctrl+Geri Al** [Metin Düzenleyici]| Edit.WordDeleteToStart |

#### <a name="file-popular-shortcuts"></a><a name="bkmk_file-popular-shortcuts"></a> Dosya: popüler kısayollar

|Komutlar|Klavye kısayolları [Özel bağlamlar]|Komut Kimliği|
|-|-|-|
|Çıkış|**Alt+F4**| File.Exit |
|Yeni dosya|**Ctrl+N**| File.NewFile |
|Yeni proje|**Ctrl+Shift+N**| File.NewProject |
|Yeni web sitesi|**Shift+Alt+N**| File.NewWebSite |
|Dosya aç|**Ctrl+O**| File.OpenFile |
|Projeyi açma|**Ctrl+Shift+O**| File.OpenProject |
|Web sitesini açma|**Shift+Alt+O**| File.OpenWebSite |
|Rename|**F2** [Takım Gezgini]| File.Rename |
|Hepsini kaydet|**Ctrl+Shift+S**| File.SaveAll |
|Seçili öğeleri kaydetme|**Ctrl+S**| File.SaveSelectedItems |
|Tarayıcıda görüntüleme|**Ctrl+Shift+W**| File.ViewinBrowser |

#### <a name="project-popular-shortcuts"></a><a name="bkmk_project-popular-shortcuts"></a>Project: popüler kısayollar

|Komutlar|Klavye kısayolları [Özel bağlamlar]|Komut Kimliği|
|-|-|-|
|Var olan öğeyi ekleme|**Shift+Alt+A**| Project.AddExistingItem |
|Yeni öğe ekleme|**Ctrl+Shift+A**| Project.AddNewItem |

#### <a name="refactor-popular-shortcuts"></a><a name="bkmk_refactor-popular-shortcuts"></a> Yeniden düzenleme: popüler kısayollar

|Komut|Klavye kısayolu [özel bağlamlar]|Komut KIMLIĞI|
|-|-|-|
|Ayıklama metodu|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |

#### <a name="tools-popular-shortcuts"></a><a name="bkmk_tools-popular-shortcuts"></a> Araçlar: popüler kısayollar

|Komut|Klavye kısayolu [özel bağlamlar]|Komut KIMLIĞI|
|-|-|-|
|İşleme ekle|**Ctrl+Alt+P**| Tools.AttachtoProcess |

#### <a name="view-popular-shortcuts"></a><a name="bkmk_view-popular-shortcuts"></a> Görünüm: popüler kısayollar

|Komutlar|Klavye kısayolları [özel bağlamlar]|Komut KIMLIĞI|
|-|-|-|
|Sınıf Görünümü|**Ctrl+Shift+C**| View.ClassView |
|Etiketi Düzenle|**F2**| View.EditLabel |
|Hata listesi|**CTRL + \\ , CTRL + E**<br /><br />ya da **CTRL + \\ , E**| View.ErrorList |
|Geriye git|**CTRL +-**| View.NavigateBackward |
|İleri git|**CTRL + SHIFT +-**| View.NavigateForward |
|Nesne tarayıcısı|**Ctrl+Alt+J**| View.ObjectBrowser |
|Çıktı|**Ctrl+Alt+O**| View.Output |
|Özellik penceresi|**F4**| View.PropertiesWindow |
|Yenile|**F5** [Takım Gezgini]| View.Refresh |
|Sunucu Gezgini|**Ctrl+Alt+S**| View.ServerExplorer |
|Akıllı etiketi göster|**CTRL +.**<br /><br />veya **SHIFT + alt + F10** [HTML Düzenleyicisi tasarım görünümü]| View.ShowSmartTag |
|Çözüm gezgini|**Ctrl+Alt+L**| View.SolutionExplorer |
|TFS Takım Gezgini|**CTRL + \\ , CTRL + ı**| View.TfsTeamExplorer |
|Araç Kutusu|**Ctrl+Alt+X**| View.Toolbox |
|Kodu görüntüle|**ENTER** [sınıf diyagramı]<br /><br />or **F7** [Ayarlar tasarımcısı]| View.ViewCode |
|Görünüm tasarımcısı|**SHIFT + F7** [HTML düzenleyici kaynak görünümü]| View.ViewDesigner |

#### <a name="window-popular-shortcuts"></a><a name="bkmk_window-popular-shortcuts"></a> Pencere: popüler kısayollar

|Komutlar|Klavye kısayolları [özel bağlamlar]|Komut KIMLIĞI|
|-|-|-|
|Belge penceresini etkinleştir|**Esc**| Window.ActivateDocumentWindow |
|Belge penceresini kapat|**Ctrl+F4**| Window.CloseDocumentWindow |
|Sonraki belge penceresi|**Ctrl+F6**| Window.NextDocumentWindow |
|Sonraki belge penceresine git|**Ctrl+Sekme**| Window.NextDocumentWindowNav |
|Sonraki bölme bölmesi|**F6**| Window.NextSplitPane |


## <a name="global-shortcuts"></a>Genel kısayollar

bu klavye kısayolları *geneldir*, bu da Visual Studio bir pencere odağa sahip olduğunda bunları kullanabileceğiniz anlamına gelir.

- [Analiz](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_analyze-global-shortcuts)
- [Mimari](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_architecture-global-shortcuts)
- [Azure](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windowsazure-global-shortcuts)
- [Derleme](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build-global-shortcuts)
- [Bağlam menülerini Sınıf Görünümü](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classview-global-shortcuts)
- [Hata Ayıklama](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug-global-shortcuts)
- [Hata ayıklama bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debugger-global-shortcuts)
- [Tanılama Merkezi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diagnostics-global-shortcuts)
- [Düzenle](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit-global-shortcuts)
- [Düzenleyici bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_editorContext-global-shortcuts)
- [Dosya](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file-global-shortcuts)
- [Yardım](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_help-global-shortcuts)
- [Yük testi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_loadtest-global-shortcuts)
- [Diğer bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_otherContext-global-shortcuts)
- [Project](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project-global-shortcuts)
- [Project ve Çözüm bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_projectContext-global-shortcuts)
- [Yeniden düzenleme](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor-global-shortcuts)
- [Çözüm Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)
- [Team](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team-global-shortcuts) (Takım)
- [Team Foundation bağlam menüleri](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFcontext-global-shortcuts)
- [Test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test-global-shortcuts)
- [Test Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)
- [Araçlar](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools-global-shortcuts)
- [Görünüm](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view-global-shortcuts)
- [Pencere](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window-global-shortcuts)

### <a name="analyze-global-shortcuts"></a><a name="bkmk_analyze-global-shortcuts"></a> Analiz: genel kısayollar

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Geriye doğru gidin|**Shift+Alt+3**| Analyze.NavigateBackward |
|İleriye gidin|**Shift+Alt+4**| Analyze.NavigateForward |

### <a name="architecture-global-shortcuts"></a><a name="bkmk_architecture-global-shortcuts"></a> Mimari: genel kısayollar

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Yeni diyagram|**Ctrl+ \\ , Ctrl+N**| Architecture.NewDiagram |

### <a name="azure-global-shortcuts"></a><a name="bkmk_windowsazure-global-shortcuts"></a> Azure: genel kısayollar

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Mobil hizmet betik işlemini yeniden deneyin|**Ctrl+Num \* , Ctrl+R**| WindowsAzure.RetryMobileServiceScriptOperation |
|Mobil hizmet betiği hata ayrıntılarını göster|**Ctrl+Num \* , Ctrl+D**| WindowsAzure.ShowMobileServiceScriptErrorDetails |

### <a name="build-global-shortcuts"></a><a name="bkmk_build-global-shortcuts"></a> Derleme: genel kısayollar

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Derleme seçimi|**Ctrl+B** (Visual Studio 2019)| Build.BuildSelection |
|Çözüm oluşturma|**Ctrl+Shift+B**| Build.BuildSolution |
|İptal|**Ctrl+Break tuşu**| Build.Cancel |
|Derlemek|**Ctrl+F7**| Build.Compile |
|Çözümde kod analizi çalıştırma|**Alt+F11**| Build.RunCodeAnalysisonSolution |

### <a name="class-view-context-menus-global-shortcuts"></a><a name="bkmk_classview-global-shortcuts"></a> Sınıf Görünümü menüleri: genel kısayollar

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Özellikler|**Alt+Enter**| ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties |

### <a name="debug-global-shortcuts"></a><a name="bkmk_debug-global-shortcuts"></a> Hata ayıklama: genel kısayollar

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Kod değişikliklerini uygulama|**Alt+F10**| Debug.ApplyCodeChanges |
|İşleme ekleme|**Ctrl+Alt+P**| Debug.AttachtoProcess |
|Otomobil|**Ctrl+Alt+V, A**| Debug.Autos |
|Hepsini kesme|**Ctrl+Alt+Break tuşu**| Debug.BreakAll |
|Kesme noktaları|**Ctrl+Alt+B**| Debug.Breakpoints |
|Çağrı yığını|**Ctrl+Alt+C**| Debug.CallStack |
|Tüm kesme noktaları silin|**Ctrl+Shift+F9**| Debug.DeleteAllBreakpoints |
|Başlat|**Alt+F2**| Debug.DiagnosticsHub.Launch |
|Demontaj|**Ctrl+Alt+D**| Debug.Disassembly |
|Dom gezgini|**Ctrl+Alt+V, D**| Debug.DOMExplorer |
|Kesme noktası etkinleştirme|**Ctrl+F9**| Debug.EnableBreakpoint |
|Özel durumlar|**Ctrl+Alt+E**| Debug.Exceptions |
|İşlev kesme noktası|**Ctrl+K, B** (Visual Studio 2019)<br />**Ctrl tuşunu basılı tutarak** + **B** (Visual Studio 2017)| Debug.FunctionBreakpoint |
|Önceki çağrıya veya IntelliTrace olayına gidin|**Ctrl+Shift+F11**| Debug.GoToPreviousCallorIntelliTraceEvent |
|Tanılamayı başlatma|**Alt+F5**| Debug.Graphics.StartDiagnostics |
|Hemen|**Ctrl+Alt+I**| Debug.Immediate |
|IntelliTrace çağrıları|**Ctrl+Alt+Y, T**| Debug.IntelliTraceCalls |
|IntelliTrace olayları|**Ctrl+Alt+Y, F**| Debug.IntelliTraceEvents |
|JavaScript konsolu|**Ctrl+Alt+V, C**| Debug.JavaScriptConsole |
|Yerli|**Ctrl+Alt+V, L**| Debug.Locals |
|İşlem birleşik giriş|**Ctrl+5**| Debug.LocationToolbar.ProcessCombo |
|Yığın çerçevesi birleşik giriş|**Ctrl+7**| Debug.LocationToolbar.StackFrameCombo |
|İş parçacığı birleşik giriş|**Ctrl+6**| Debug.LocationToolbar.ThreadCombo |
|Geçerli iş parçacığı bayraklı durumunu açma//sn'ye geçiş|**Ctrl+8**| Debug.LocationToolbar.ToggleCurrentThreadFlaggedState |
|Bayraklı iş parçacıklarını geçişli olarak değiştir|**Ctrl+9**| Debug.LocationToolbar.ToggleFlaggedThreads |
|Bellek 1|**Ctrl+Alt+M, 1**| Debug.Memory1 |
|Bellek 2|**Ctrl+Alt+M, 2**| Debug.Memory2 |
|Bellek 3|**Ctrl+Alt+M, 3**| Debug.Memory3 |
|Bellek 4|**Ctrl+Alt+M, 4**| Debug.Memory4 |
|Modül|**Ctrl+Alt+U**| Debug.Modules |
|Paralel yığınlar|**Ctrl+Shift+D, S**| Debug.ParallelStacks |
|Paralel izleme 1|**Ctrl+Shift+D, 1**| Debug.ParallelWatch1 |
|Paralel izleme 2|**Ctrl+Shift+D, 2**| Debug.ParallelWatch2 |
|Paralel izleme 3|**Ctrl+Shift+D, 3**| Debug.ParallelWatch3 |
|Paralel izleme 4|**Ctrl+Shift+D, 4**| Debug.ParallelWatch4 |
|İşlemler|**Ctrl+Alt+Z**| Debug.Processes |
|Hızlı izleme|**Shift+F9** veya **Ctrl+Alt+Q**| Debug.QuickWatch |
|İşleme yeniden ekleme|**Shift+Alt+P**| Debug.ReattachtoProcess |
|Windowsapp'i yenileme|**Ctrl+Shift+R**| Debug.RefreshWindowsapp |
|Kayd -eder|**Ctrl+Alt+G**| Debug.Registers |
|Yeniden başlat|**Ctrl+Shift+F5**| Debug.Restart |
|İmleç için çalıştır|**Ctrl+F10**| Debug.RunToCursor |
|Sonraki deyimi ayarla|**Ctrl+Shift+F10**| Debug.SetNextStatement |
|Kod haritasında çağrı yığınını göster|**CTRL + SHIFT + '**| Debug.ShowCallStackonCodeMap |
|Sonraki ifadeyi göster|**Alt + NUM** *| Debug.ShowNextStatement |
|Başlangıç|**F5**| Debug.Start |
|Windows Phone uygulama analizini Başlat|**Alt+F1**| Debug.StartWindowsPhoneApplicationAnalysis |
|Hata ayıklama olmadan Başlat|**Ctrl+F5**| Debug.StartWithoutDebugging |
|Adımla|**F11**| Debug.StepInto |
|Geçerli işleme adımla|**Ctrl+Alt+F11**| Debug.StepIntoCurrentProcess |
|Belirli bir adımla|**Shift+Alt+F11**| Debug.StepIntoSpecific |
|Dışarı adımla|**Shift+F11**| Debug.StepOut |
|Geçerli işlemi adımla|**Ctrl+Shift+Alt+F11**| Debug.StepOutCurrentProcess |
|Adımla|**F10** (hata ayıklama sırasında: eylem üzerinde bir adım gerçekleştirir)| Debug.StepOver |
|Adımla|**F10** (hata ayıklama olmadığında: Kullanıcı kodunun ilk satırında hata ayıklamaya başlar ve duraklar)| Debug.StepOver |
|Geçerli işlemin üzerinde adımla|**Ctrl+Alt+F10**| Debug.StepOverCurrentProcess |
|Hata ayıklamayı Durdur|**Shift+F5**| Debug.StopDebugging |
|Performans analizini durdur|**Shift+Alt+F2**| Debug.StopPerformanceAnalysis |
|Görevler|**Ctrl+Shift+D, K**| Debug.Tasks |
|İş Parçacıkları|**Ctrl+Alt+H**| Debug.Threads |
|Kesme noktasını aç|**F9**| Debug.ToggleBreakpoint |
|Ayrıştırılmış derlemeyi değiştirme|**Ctrl+F11**| Debug.ToggleDisassembly |
|1 izleyin|**Ctrl+Alt+W, 1**| Debug.Watch1 |
|2. gözcü|**CTRL + ALT + W, 2**| Debug.Watch2 |
|3. gözcü|**CTRL + ALT + W, 3**| Debug.Watch3 |
|4 izleyin|**CTRL + ALT + W, 4**| Debug.Watch4 |

### <a name="debugger-context-menus-global-shortcuts"></a><a name="bkmk_debugger-global-shortcuts"></a> Hata ayıklayıcı bağlam menüleri: genel kısayollar

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Sil|**Alt+F9, D**| DebuggerContextMenus.BreakpointsWindow.Delete |
|Ayrıştırılmış koda git|**Alt+F9, A**| DebuggerContextMenus.BreakpointsWindow.GoToDisassembly |
|Kaynak koduna git|**Alt+F9, S**| DebuggerContextMenus.BreakpointsWindow.GoToSourceCode |

### <a name="diagnostics-hub-global-shortcuts"></a><a name="bkmk_diagnostics-global-shortcuts"></a> Tanılama Merkezi: genel kısayollar

|Komut|Klavye kısayolu|Komut KIMLIĞI|
|-|-|-|
|Toplamayı durdur|**Ctrl+Alt+F2**| DiagnosticsHub.StopCollection |

### <a name="edit-global-shortcuts"></a><a name="bkmk_edit-global-shortcuts"></a> Düzenle: genel kısayollar

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Kopyala|**Ctrl+C**<br /><br /> veya<br /><br /> **Ctrl+Ins**| Edit.Copy |
|Kes|**Ctrl+X**<br /><br /> veya<br /><br /> **Shift+Delete**| Edit.Cut |
|Döngü pano halkası|**Ctrl+Shift+V**<br /><br /> veya<br /><br /> **Ctrl+Shift+Ins**| Edit.CycleClipboardRing |
|Sil|**Silme**| Edit.Delete |
|Yinele|**Ctrl+D**| Edit.Duplicate |
|Bul|**Ctrl+F**| Edit.Find |
|Tüm başvuruları bulma|**Shift+F12**| Edit.FindAllReferences |
|Dosyalarda bulma|**Ctrl+Shift+F**| Edit.FindinFiles |
|Sonrakini bul|**F3**| Edit.FindNext |
|Sonraki seçileni bul|**Ctrl+F3**| Edit.FindNextSelected |
|Öncekini bul|**Shift+F3**| Edit.FindPrevious |
|Önceki seçileni bul|**Ctrl+Shift+F3**| Edit.FindPreviousSelected |
|Metot oluşturma|**Ctrl+K, Ctrl+M**| Edit.GenerateMethod |
|Git|**Ctrl+G**| Edit.GoTo |
|Tamam'a gidin|**Ctrl+veya** **Ctrl+T**| Edit.GoToAll |
|Bildirime git|**Ctrl+F12**| Edit.GoToDeclaration |
|Tanıma git|**F12**| Edit.GoToDefinition |
|Üyeye git|**Ctrl+1, Ctrl+M** veya **Ctrl+1, M** veya **Alt+ \\**| Edit.GoToMember |
|Sonraki konuma gidin|**F8** (Hata Listesi veya Çıkış penceresinde sonraki hata)| Edit.GoToNextLocation |
|Ön konuma gidin|**Shift+F8** (Hata Listesi veya Çıkış penceresinde önceki hata)| Edit.GoToPrevLocation |
|Kod parçacığı ekleme|**Ctrl+K, Ctrl+X**| Edit.InsertSnippet |
|Denetimi aşağı taşıma|**Ctrl+Aşağı Ok**| Edit.MoveControlDown |
|Denetimi aşağı kılavuza taşıma|**Aşağı Ok**| Edit.MoveControlDownGrid |
|Denetimi sola taşıma|**Ctrl+Sol Ok**| Edit.MoveControlLeft |
|Denetimi sol kılavuza taşıma|**Sol Ok**| Edit.MoveControlLeftGrid |
|Denetimi sağa taşıma|**Ctrl+Sağ Ok**| Edit.MoveControlRight |
|Denetimi sağ kılavuza taşıma|**Sağ Ok**| Edit.MoveControlRightGrid |
|Denetimi yukarı taşıma|**Ctrl+Yukarı Ok**| Edit.MoveControlUp |
|Denetimi yukarı kılavuza taşıma|**Yukarı Ok**| Edit.MoveControlUpGrid |
|Sonraki yer işareti|**Ctrl+K, Ctrl+N**| Edit.NextBookmark |
|Klasördeki sonraki yer işareti|**Ctrl+Shift+K, Ctrl+Shift+N**| Edit.NextBookmarkInFolder |
|Dosya aç|**Ctrl+Shift+G** (İmleç altında dosya adını açar)| Edit.OpenFile |
|Yapıştır|**Ctrl+V**<br /><br /> veya<br /><br /> **Shift+Ins**| Edit.Paste |
|Önceki yer işareti|**Ctrl+K, Ctrl+P**| Edit.PreviousBookmark |
|Klasördeki önceki yer işareti|**Ctrl+Shift+K, Ctrl+Shift+P**| Edit.PreviousBookmarkInFolder |
|Hızlı bul simgesi|**Shift+Alt+F12**| Edit.QuickFindSymbol |
|Yinele|**Ctrl+Y**<br /><br /> veya<br /><br /> **Ctrl+Shift+Z**<br /><br /> veya<br /><br /> **Shift+Alt+Geri Al tuşu**| Edit.Redo |
|Uzak başvuruları Yenile|**Ctrl+Shift+J**| Edit.RefreshRemoteReferences |
|Değiştir|**Ctrl+H**| Edit.Replace |
|Dosyalarda Değiştir|**Ctrl+Shift+H**| Edit.ReplaceinFiles |
|Tümünü seç|**Ctrl+A**| Edit.SelectAll |
|Sonraki denetimi Seç|**Sekme**| Edit.SelectNextControl |
|Önceki denetimi Seç|**Shift+Sekme Tuşu**| Edit.SelectPreviousControl |
|Döşeme kılavuzunu göster|**Enter**| Edit.ShowTileGrid |
|Denetimi aşağı doğru Boyutlandır|**Ctrl+Shift+Aşağı Ok**| Edit.SizeControlDown |
|Denetimi alt kılavuza kadar Boyutlandır|**Shift+Aşağı Ok**| Edit.SizeControlDownGrid |
|Denetimi sola Boyutlandır|**Ctrl+Shift+Sol Ok**| Edit.SizeControlLeft |
|Denetim sol kılavuza kadar Boyutlandır|**Shift+Sol Ok**| Edit.SizeControlLeftGrid |
|Denetimi sağa Boyutlandır|**Ctrl+Shift+Sağ Ok**| Edit.SizeControlRight |
|Denetim sağ kılavuzunu Boyutlandır|**Shift+Sağ Ok**| Edit.SizeControlRightGrid |
|Denetimin boyutunu ayarla|**Ctrl+Shift+Yukarı Ok**| Edit.SizeControlUp |
|Denetimi yukarı kılavuza göre boyutlandır|**Shift+Yukarı Ok**| Edit.SizeControlUpGrid |
|Aramayı durdur|**Alt+F3, S**| Edit.StopSearch |
|Şununla Çevrele|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Geri Al|**CTRL + Z**<br /><br /> veya<br /><br /> **Alt+Geri Al tuşu**| Edit.Undo |

### <a name="editor-context-menus-global-shortcuts"></a><a name="bkmk_editorContext-global-shortcuts"></a> Düzenleyici bağlam menüleri: genel kısayollar

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Kesme noktası koşulları|**Alt + F9, C**| EditorContextMenus. CodeWindow. Breakpoint. BreakpointConditions |
|Kesme noktası etiketlerini Düzenle|**Alt+F9, L**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels |
|Geçici kesme noktası ekle|**SHIFT + alt + F9, T**| EditorContextMenus. CodeWindow. Breakpoint. InsertTemporaryBreakpoint |
|Öğeyi göster|**CTRL + '**| EditorContextMenus.CodeWindow.CodeMap.ShowItem |
|Yürütme|**Ctrl+Alt+F5**| EditorContextMenus.CodeWindow.Execute |
|Görünüme git|**Ctrl+M, Ctrl+G**| EditorContextMenus.CodeWindow.GoToView |
|Üstbilgi kodu dosyasını değiştirme|**CTRL + K, CTRL + O** (harf ' O ')| EditorContextMenus.CodeWindow.ToggleHeaderCodeFile |
|Çağrı hiyerarşisini görüntüle|**Ctrl+K, Ctrl+T**<br /><br /> veya<br /><br /> **Ctrl+K, T**| EditorContextMenus.CodeWindow.ViewCallHierarchy |

### <a name="file-global-shortcuts"></a><a name="bkmk_file-global-shortcuts"></a> Dosya: genel kısayollar

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Çıkış|**Alt+F4**| File.Exit |
|Yeni dosya|**Ctrl+N**| File.NewFile |
|Yeni proje|**Ctrl+Shift+N**| File.NewProject |
|Yeni Web sitesi|**Shift+Alt+N**| File.NewWebSite |
|Dosya Aç|**CTRL + O** (harf ' O ')| File.OpenFile |
|Projeyi açma|**CTRL + SHIFT + O** (harf ' O ')| File.OpenProject |
|Web sitesi aç|**SHIFT + alt + O** (harf ' O ')| File.OpenWebSite |
|Yazdır|**Ctrl+P**| File.Print |
|Tümünü Kaydet|**Ctrl+Shift+S**| File.SaveAll |
|Seçili öğeleri kaydet|**Ctrl+S**| File.SaveSelectedItems |
|Tarayıcıda görüntüleme|**Ctrl+Shift+W**| File.ViewinBrowser |

### <a name="help-global-shortcuts"></a><a name="bkmk_help-global-shortcuts"></a> Yardım: genel kısayollar

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Yardım içeriği ekleme ve kaldırma|**Ctrl+Alt+F1**| Help.AddandRemoveHelpContent |
|F1 yardımı|**F1**| Help.F1Help |
|Yardım 'ı görüntüle|**Ctrl+F1**| Help.ViewHelp |
|Pencere yardımı|**Shift+F1**| Help.WindowHelp |

### <a name="load-test-global-shortcuts"></a><a name="bkmk_loadtest-global-shortcuts"></a> Yük testi: genel kısayollar

|Komut|Klavye kısayolu|Komut KIMLIĞI|
|-|-|-|
|Sayaç bölmesine geç|**Ctrl+R, Q**| LoadTest.JumpToCounterPane |

### <a name="other-context-menus-global-shortcuts"></a><a name="bkmk_otherContext-global-shortcuts"></a> Diğer bağlam menüleri: genel kısayollar

|Komut|Klavye kısayolu|Komut KIMLIĞI|
|-|-|-|
|Yeni Diyagram Ekle|**Ekle**| OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram |

### <a name="project-global-shortcuts"></a><a name="bkmk_project-global-shortcuts"></a>Project: genel kısayollar

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Var olan öğeyi Ekle|**Shift+Alt+A**| Project.AddExistingItem |
|Yeni öğe Ekle|**Ctrl+Shift+A**| Project.AddNewItem |
|Sınıf Sihirbazı|**Ctrl+Shift+X**| Project.ClassWizard |
|Geçersiz kıl|**Ctrl+Alt+Ins**| Project.Override |
|Değişiklikleri Önizle|**Alt +;** sonra **alt + C**| Project.Previewchanges |
|Seçili dosyaları Yayımla|**Alt +;** sonra **alt + P**| Project.Publishselectedfiles |
|Seçili dosyaları sunucudan Değiştir|**Alt +;** sonra **Alt + R**| Project.Replaceselectedfilesfromserver |

### <a name="project-and-solution-context-menus-global-shortcuts"></a><a name="bkmk_projectContext-global-shortcuts"></a>Project ve çözüm bağlam menüleri: genel kısayollar

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Aşağı taşı|**Alt+Aşağı Ok**| ProjectandSolutionContextMenus.Item.MoveDown |
|Yukarı taşı|**Alt+Yukarı Ok**| ProjectandSolutionContextMenus.Item.MoveUp |

### <a name="refactor-global-shortcuts"></a><a name="bkmk_refactor-global-shortcuts"></a> Yeniden düzenleme: genel kısayollar

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Alanı kapsülleme|**Ctrl+R, Ctrl+E**| Refactor.EncapsulateField |
|Ayıklama arabirimi|**Ctrl+R, Ctrl+I**| Refactor.ExtractInterface |
|Ayıklama metodu|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |
|Parametreleri Kaldır|**Ctrl+R, Ctrl+V**| Refactor.RemoveParameters |
|Rename|**Ctrl+R, Ctrl+R**| Refactor.Rename |
|Parametreleri yeniden sırala|**CTRL + R, CTRL + O** (harf ' O ')| Refactor.ReorderParameters |

### <a name="solution-explorer-global-shortcuts"></a><a name="bkmk_solutionexplorerGLOBAL"></a> Çözüm Gezgini: genel kısayollar

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Açık dosyalar filtresi|**CTRL + [**, **O** (harf ' O ')<br /><br /> veya<br /><br /> **CTRL + [**, **CTRL + O** (harf ' O ')| SolutionExplorer.OpenFilesFilter |
|Bekleyen değişiklikler filtresi|**CTRL + [**, **P**<br /><br /> veya<br /><br /> **CTRL + [**, **CTRL + P**| SolutionExplorer.PendingChangesFilter |
|Etkin belge ile Eşitle|**CTRL + [**, **S**<br /><br /> veya<br /><br /> **CTRL + [**, **CTRL + S**| SolutionExplorer.SyncWithActiveDocument |

### <a name="team-global-shortcuts"></a><a name="bkmk_team-global-shortcuts"></a> Takım: genel kısayollar

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Git dallarına git|**CTRL + 0** (sıfır), **CTRL + N**<br /><br /> veya<br /><br /> **Ctrl+0, N**| Team.Git.GoToGitBranches |
|Git değişikliklerine git|**CTRL + 0** (sıfır), **CTRL + G**<br /><br /> veya<br /><br /> **Ctrl+0, G**| Team.Git.GoToGitChanges |
|Git yürütmelerine git|**CTRL + 0** (sıfır), **CTRL + O** (harf ' O ')<br /><br /> veya<br /><br /> **Ctrl+0, O**| Team.Git.GoToGitCommits |
|Takım Gezgini araması|**CTRL + '**| Team.TeamExplorerSearch |

### <a name="team-foundation-context-menus-global-shortcuts"></a><a name="bkmk_TFcontext-global-shortcuts"></a> Team Foundation bağlam menüleri: genel kısayollar

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Derlemeler 'e git|**CTRL + 0** (sıfır), **CTRL + B**<br /><br /> veya<br /><br /> **Ctrl+0, B**| TeamFoundationContextMenus.Commands.GoToBuilds |
|Bağlan 'a git|**CTRL + 0** (sıfır), **CTRL + C**<br /><br /> veya<br /><br /> **Ctrl+0, C**| TeamFoundationContextMenus.Commands.GoToConnect |
|Belgelere git|**CTRL + 0** (sıfır), **CTRL + D**<br /><br /> veya<br /><br /> **Ctrl+0, D**| TeamFoundationContextMenus.Commands.GoToDocuments |
|Girişe git|**CTRL + 0** (sıfır), **CTRL + H**<br /><br /> veya<br /><br /> **Ctrl+0, H**| TeamFoundationContextMenus.Commands.GoToHome |
|Çalışmam 'a git|**CTRL + 0** (sıfır), **CTRL + ı**<br /><br /> veya<br /><br /> **Ctrl+0, M**| TeamFoundationContextMenus.Commands.GoToMyWork |
|Bekleyen değişikliklere git|**CTRL + 0** (sıfır), **CTRL + P**<br /><br /> veya<br /><br /> **Ctrl+0, P**| TeamFoundationContextMenus.Commands.GoToPendingChanges |
|Raporlara gitme|**Ctrl+0** (sıfır), **Ctrl+R**<br /><br /> veya<br /><br /> **Ctrl+0, R**| TeamFoundationContextMenus.Commands.GoToReports |
|Ayarlara gidin|**Ctrl+0** (sıfır), **Ctrl+S**<br /><br /> veya<br /><br /> **Ctrl+0, S**| TeamFoundationContextMenus.Commands.GoToSettings |
|Web erişimine gidin|**Ctrl+0** (sıfır), **Ctrl+A**<br /><br /> veya<br /><br /> **Ctrl+0, A**| TeamFoundationContextMenus.Commands.GoToWebAccess |
|İş öğelerine gitme|**Ctrl+0** (sıfır), **Ctrl+W**<br /><br /> veya<br /><br /> **Ctrl+0, W**| TeamFoundationContextMenus.Commands.GoToWorkItems |

### <a name="test-global-shortcuts"></a><a name="bkmk_test-global-shortcuts"></a> Test: genel kısayollar

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Kodlanmış ui test oluşturucusu kullanma|**Ctrl+ \\ , Ctrl+C**| Test.UseCodedUITestBuilder |
|Mevcut eylem kaydını kullanma|**Ctrl+ \\ , Ctrl+A**| Test.UseExistingActionRecording |

### <a name="test-explorer-global-shortcuts"></a><a name="bkmk_testexplorerGLOBAL"></a> Test Gezgini: genel kısayollar

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Tüm testlerde hata ayıklama|**Ctrl+R, Ctrl+A**| TestExplorer.DebugAllTests |
|Bağlamdaki tüm testlerde hata ayıklama|**Ctrl+R, Ctrl+T**| TestExplorer.DebugAllTestsInContext |
|Son çalıştırmada hata ayıklama|**Ctrl+R, D**| TestExplorer.DebugLastRun |
|Son çalıştırmayı yinele|**Ctrl+R, L**| TestExplorer.RepeatLastRun |
|Tüm testleri çalıştırma|**Ctrl+R, A**| TestExplorer.RunAllTests |
|Tüm testleri bağlam içinde çalıştırma|**Ctrl+R, T**| TestExplorer.RunAllTestsInContext |
|Test gezginini göster|**Ctrl+E, T**| TestExplorer.ShowTestExplorer |
|Aç sekmesi|**Ctrl+E, L**| LiveUnitTesting.OpenTab |
|Kod kapsamı sonuçları|**Ctrl+E, C**| Test.CodeCoverageResults |

### <a name="tools-global-shortcuts"></a><a name="bkmk_tools-global-shortcuts"></a> Araçlar: genel kısayollar

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|İşleme ekle|**Ctrl+Alt+P**| Tools.AttachtoProcess |
|Kod parçacıkları yöneticisi|**Ctrl+K, Ctrl+B**| Tools.CodeSnippetsManager |
|Gc'ye zorlama|**Ctrl+Shift+Alt+F12, Ctrl+Shift+Alt+F12**| Tools.ForceGC |

### <a name="view-global-shortcuts"></a><a name="bkmk_view-global-shortcuts"></a> Görünüm: genel kısayollar

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Tüm pencereler|**Shift+Alt+M**| View.AllWindows |
|Mimari gezgini|**Ctrl+ \\ , Ctrl+R**| View.ArchitectureExplorer |
|Geri|**Alt+Sol Ok** (İşlevler, Metin Düzenleyicisi'nde View.NavigateBackward'tan farklı)| View.Backward |
|Yer işareti penceresi|**Ctrl+K, Ctrl+W**| View.BookmarkWindow |
|Sonrakine göz at|**Ctrl+Shift+1**| View.BrowseNext |
|Öncekine göz atma|**Ctrl+Shift+2**| View.BrowsePrevious |
|Çağrı hiyerarşisi|**Ctrl+Alt+K**| View.CallHierarchy |
|Sınıf Görünümü|**Ctrl+Shift+C**| View.ClassView |
|Sınıf görünümü arama Birleşik giriş kutusuna git|**Ctrl+K, Ctrl+V**| View.ClassViewGoToSearchCombo |
|Kod tanımı penceresi|**CTRL + \\ , D**<br /><br /> veya<br /><br /> **CTRL + \\ , CTRL + D**| View.CodeDefinitionWindow |
|Komut penceresi|**Ctrl+Alt+A**| View.CommandWindow |
|Veri kaynakları|**Shift+Alt+D**| View.DataSources |
|Belge ana hattı|**Ctrl+Alt+T**| View.DocumentOutline |
|Etiketi Düzenle|**F2**| View.EditLabel |
|Hata listesi|**CTRL + \\ , E**<br /><br /> veya<br /><br /> **CTRL + \\ , CTRL + E**| View.ErrorList |
|F# etkileşimli|**Ctrl+Alt+F**| View.F#Interactive |
|Sembol sonuçları bul|**Ctrl+Alt+F12**| View.FindSymbolResults |
|İleri|**Alt + sağ ok**  (metin düzenleyicisinde View. navigateforward öğesinden farklı işlevler)| View.Forward |
|İleri git bağlamı|**Ctrl+Shift+7**| View.ForwardBrowseContext |
|Tam ekran|**Shift+Alt+Enter**| View.FullScreen |
|Geriye git|**CTRL +-**| View.NavigateBackward |
|İleri git|**CTRL + SHIFT +-**| View.NavigateForward |
|Sonraki hata|**Ctrl+Shift+F12**| View.NextError |
|Bildirimler|**Ctrl+W, N**<br /><br /> veya<br /><br /> **Ctrl+W, Ctrl+N**| View.Notifications |
|Nesne tarayıcısı|**Ctrl+Alt+J**| View.ObjectBrowser |
|Nesne tarayıcısı arama açılan kutusuna git|**Ctrl+K, Ctrl+R**| View.ObjectBrowserGoToSearchCombo |
|Çıktı|**Ctrl + Alt + O** (harf ' O ')| View.Output |
|Pop içerik tarama bağlamı|**CTRL + SHIFT + 8** (yalnızca C++)| View. PopBrowseContext |
|Özellik penceresi|**F4**| View.PropertiesWindow |
|Özellik sayfaları|**Shift+F4**| View.PropertyPages |
|Kaynak görünümü|**Ctrl+Shift+E**| View.ResourceView |
|Sunucu Gezgini|**Ctrl+Alt+S**| View.ServerExplorer |
|Akıllı etiketi göster|**Shift+Alt+F10**<br /><br /> veya<br /><br /> **CTRL +.**| View.ShowSmartTag |
|Çözüm gezgini|**Ctrl+Alt+L**| View.SolutionExplorer |
|SQL server nesne gezgini|**CTRL + \\ , CTRL + S**| View.SQLServerObjectExplorer |
|Görev listesi|**CTRL + \\ , T**<br /><br /> veya<br /><br /> **CTRL + \\ , CTRL + T**| View.TaskList |
|TFS Takım Gezgini|**CTRL + \\ , CTRL + ı**| View.TfsTeamExplorer |
|Araç Kutusu|**Ctrl+Alt+X**| View.Toolbox |
|UML Model Gezgini|**CTRL + \\ , CTRL + U**| View.UMLModelExplorer |
|Kodu görüntüle|**F7**| View.ViewCode |
|Görünüm tasarımcısı|**Shift+F7**| View.ViewDesigner |
|Web tarayıcısı|**Ctrl+Alt+R**| View.WebBrowser |
|Yakınlaştır|**CTRL + SHIFT +.**| View.ZoomIn |
|Uzaklaştır|**CTRL + SHIFT +,**| View.ZoomOut |
|Test Gezginini göster|**CTRL + E, T**| TestExplorer. ShowTestExplorer |

### <a name="window-global-shortcuts"></a><a name="bkmk_window-global-shortcuts"></a> Pencere: genel kısayollar

|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Belge penceresini etkinleştir|**Esc**| Window.ActivateDocumentWindow |
|Seçime sekme ekle|**Ctrl+Shift+Alt+Ara Çubuğu**| Window.AddTabtoSelection |
|Belge penceresini kapat|**Ctrl+F4**| Window.CloseDocumentWindow |
|Araç penceresini kapat|**Shift+Esc**| Window.CloseToolWindow |
|Sekmeyi açık tut|**Ctrl+Alt+Home**| Window.KeepTabOpen |
|Gezinti çubuğuna taşı|**Ctrl+F2**| Window.MovetoNavigationBar |
|Sonraki belge penceresi|**Ctrl+F6**| Window.NextDocumentWindow |
|Sonraki belge penceresine git|**Ctrl+Sekme**| Window.NextDocumentWindowNav |
|Sonraki bölme|**Alt+F6**| Window.NextPane |
|Sonraki bölme bölmesi|**F6**| Window.NextSplitPane |
|Sonraki sekme|**Ctrl+Alt+PgDn**<br /><br /> veya<br /><br /> **Ctrl+PgDn**| Window.NextTab |
|Sonraki sekme ve Seçime Ekle|**Ctrl+Shift+Alt+PgDn**| Window.NextTabandAddtoSelection |
|Sonraki araç penceresine git|**Alt+F7**| Window.NextToolWindowNav |
|Önceki belge penceresi|**Ctrl+Shift+F6**| Window.PreviousDocumentWindow |
|Önceki belge penceresine git|**Ctrl+Shift+Sekme**| Window.PreviousDocumentWindowNav |
|Önceki bölme|**Shift+Alt+F6**| Window.PreviousPane |
|Önceki bölme bölmesi|**Shift+F6**| Window.PreviousSplitPane |
|Önceki sekme|**Ctrl+Alt+PgUp**<br /><br /> veya<br /><br /> **Ctrl+PgUp**| Window.PreviousTab |
|Önceki sekme ve Seçime Ekle|**Ctrl+Shift+Alt+PgUp**| Window.PreviousTabandAddtoSelection |
|Önceki araç penceresi gezintisi|**Shift+Alt+F7**| Window.PreviousToolWindowNav |
|Hızlı Başlat|**Ctrl+Q**| Window.QuickLaunch |
|Önceki kategoriyi Hızlı Başlat|**Ctrl+Shift+Q**| Window.QuickLaunchPreviousCategory |
|Dock menüsünü göster|**Alt +-**| Window.ShowDockMenu |
|Ex MDI dosya listesini göster|**Ctrl+Alt+Aşağı Ok**| Window.ShowEzMDIFileList |
|Çözüm gezgini araması|**Ctrl+;**| Window.SolutionExplorerSearch |
|Pencere araması|**Alt+'**| Window.WindowSearch |

## <a name="context-specific-shortcuts"></a>Bağlama özgü kısayollar
Bu klavye kısayolları bağlama özgü olduğu için bunları bir proje türüne, programlama diline veya platforma Visual Studio menüler ve öğelerle birlikte kullanabilirsiniz.

- [ADO.NET Varlık Veri Modeli Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_adonet-entity-data-model-designer-context-specific-shortcuts)
- [Sınıf Diyagramı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_class-diagram-context-specific-shortcuts)
- [Kodlanmış UI Test Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_coded-ui-test-editor-context-specific-shortcuts)
- [Veri Kümesi Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_dataset-editor-context-specific-shortcuts)
- [Fark Görüntüleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_difference-viewer-context-specific-shortcuts)
- [DOM Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_dom-explorer-context-specific-shortcuts)
- [F# Etkileşimli](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_f-interactive-context-specific-shortcuts)
- [Grafik Belgesi Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_graph-document-editor-context-specific-shortcuts)
- [Grafik Tanılama](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_graphics-diagnostics-context-specific-shortcuts)
- [HTML Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_html-editor-context-specific-shortcuts)
- [HTML Düzenleyicisi Tasarım Görünümü](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_html-editor-design-view-context-specific-shortcuts)
- [HTML Düzenleyicisi Kaynak Görünümü](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_html-editor-source-view-context-specific-shortcuts)
- [Katman Diyagramı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_layer-diagram-context-specific-shortcuts)
- [Yönetilen Kaynaklar Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_managed-resources-editor-context-specific-shortcuts)
- [DüzenleyiciYi Birleştir Penceresi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_merge-editor-window-context-specific-shortcuts)
- [Microsoft SQL Server Veri Araçları, Şema Karşılaştırma](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_microsoft-sql-server-data-tools-schema-compare-context-specific-shortcuts)
- [Microsoft SQL Server Veri Araçları, Tablo Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_microsoft-sql-server-data-tools-table-designer-context-specific-shortcuts)
- [Microsoft SQL Server Veri Araçları, T-SQL Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_microsoft-sql-server-data-tools-t-sql-editor-context-specific-shortcuts)
- [Microsoft SQL Server Veri Araçları, T-SQL PDW Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_microsoft-sql-server-data-tools-t-sql-pdw-editor-context-specific-shortcuts)
- [Sayfa Denetçisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_page-inspector-context-specific-shortcuts)
- [Sorgu Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_query-designer-context-specific-shortcuts)
- [Sorgu Sonuçları](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_query-results-context-specific-shortcuts)
- [Rapor Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_report-designer-context-specific-shortcuts)
- [Sıralı Diyagram](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_sequence-diagram-context-specific-shortcuts)
- [Ayarlar Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_settings-designer-context-specific-shortcuts)
- [Çözüm Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solution-explorer-context-specific-shortcuts)
- [Takım Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team-explorer-context-specific-shortcuts)
- [Test Gezgini](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test-explorer-context-specific-shortcuts)
- [Metin Düzenleyici](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_text-editor-context-specific-shortcuts)
- [UML Etkinlik Diyagramı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_uml-activity-diagram-context-specific-shortcuts)
- [UML Sınıf Diyagramı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_uml-class-diagram-context-specific-shortcuts)
- [UML Bileşen Diyagramı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_uml-component-diagram-context-specific-shortcuts)
- [UML Kullanım Durumu Diyagramı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_uml-use-case-diagram-context-specific-shortcuts)
- [VC Hızlandırıcı Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vc-accelerator-editor-context-specific-shortcuts)
- [VC İletişim Kutusu Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vc-dialog-editor-context-specific-shortcuts)
- [VC Görüntü Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vc-image-editor-context-specific-shortcuts)
- [VC Dize Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_vc-string-editor-context-specific-shortcuts)
- [Görünüm Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view-designer-context-specific-shortcuts)
- [Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_visual-studio-context-specific-shortcuts)
- [Windows Form Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windows-forms-designer-context-specific-shortcuts)
- [Çalışma Öğesi Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_work-item-editor-context-specific-shortcuts)
- [Çalışma Öğesi Sorgu Görünümü](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_work-item-query-view-context-specific-shortcuts)
- [Çalışma Öğesi Sonuçlar Görünümü](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_work-item-results-view-context-specific-shortcuts)
- [İş Akışı Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_workflow-designer-context-specific-shortcuts)
- [XAML Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_xaml-ui-designer-context-specific-shortcuts)
- [XML (Metin) Düzenleyicisi](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_xml-text-editor-context-specific-shortcuts)
- [XML Şema Tasarımcısı](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_xml-schema-designer-context-specific-shortcuts)

### <a name="adonet-entity-data-model-designer-context-specific-shortcuts"></a><a name="bkmk_adonet-entity-data-model-designer-context-specific-shortcuts"></a>ADO.NET Varlık Veri Modeli Tasarımcısı: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:

|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Aşağı|**Alt+Aşağı Ok**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down |
|Aşağı 5|**Alt+PgDn**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down5 |
|Alta|**Alt+End**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToBottom |
|Üste|**Alt+Home**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToTop |
|Yukarı|**Alt+Yukarı Ok**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up |
|Yukarı 5|**Alt+PgUp**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5 |
|Rename|**Ctrl+R, R**| OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename |
|Diyagramdan kaldır|**Shift+Del**| OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram |
|Varlık veri modeli tarayıcısı|**Ctrl+1**| View.EntityDataModelBrowser |
|Varlık veri modeli eşleme ayrıntıları|**Ctrl+2**| View.EntityDataModelMappingDetails |

### <a name="class-diagram-context-specific-shortcuts"></a><a name="bkmk_class-diagram-context-specific-shortcuts"></a> Sınıf diyagramı: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Daralt|**Num -**| ClassDiagram.Collapse |
|Genişlet|**NUM +**| ClassDiagram.Expand |
|Sil|**Ctrl+Del**| Edit.Delete |
|Expand temel tür listesini Daralt|**Shift+Alt+B**| Edit.ExpandCollapseBaseTypeList |
|Lolipop 'a git|**Shift+Alt+L**| Edit.NavigateToLollipop |
|Diyagramdan kaldır|**Silme**| Edit.RemovefromDiagram |
|Kodu görüntüle|**Enter**| View.ViewCode |

### <a name="coded-ui-test-editor-context-specific-shortcuts"></a><a name="bkmk_coded-ui-test-editor-context-specific-shortcuts"></a> Kodlanmış UI Test Düzenleyicisi: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Başvuruyu panoya kopyala|**Ctrl+C**| OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard |
|Öncesine gecikme Ekle|**Ctrl+Alt+D**| OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore |
|Tümünü Bul|**Shift+Alt+L**| OtherContextMenus.UITestEditorContextMenu.LocateAll |
|UI denetimini bulma|**Ctrl+Shift+L**| OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl |
|Kodu taşı|**Ctrl+Alt+C**| OtherContextMenus.UITestEditorContextMenu.Movecode |
|Yeni bir yönteme Böl|**Ctrl+Shift+T**| OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod |

### <a name="dataset-editor-context-specific-shortcuts"></a><a name="bkmk_dataset-editor-context-specific-shortcuts"></a> Veri kümesi Düzenleyicisi: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Sütun Ekle|**Ekle**| OtherContextMenus.ColumnContext.InsertColumn |
|Sütun|**Ctrl+L**| OtherContextMenus.DbTableContext.Add.Column |

### <a name="difference-viewer-context-specific-shortcuts"></a><a name="bkmk_difference-viewer-context-specific-shortcuts"></a> Fark Görüntüleyicisi: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Kırpma boşluğunu yoksay|**CTRL + \\ , CTRL + Ara çubuğu**| Diff.IgnoreTrimWhitespace |
|Satır içi görünüm|**CTRL + \\ , CTRL + 1**| Diff.InlineView |
|Yalnızca sol görünüm|**CTRL + \\ , CTRL + 3**| Diff.LeftOnlyView |
|Sonraki fark|**F8**| Diff.NextDifference |
|Önceki fark|**Shift+F8**| Diff.PreviousDifference |
|Yalnızca sağ görünüm|**CTRL + \\ , Ctrl + 4**| Diff.RightOnlyView |
|Yan yana görünüm|**CTRL + \\ , CTRL + 2**| Diff.SideBySideView |
|Sol ve sağ arasında geçiş yap|**CTRL + \\ , CTRL + SEKME**| Diff.SwitchBetweenLeftAndRight |
|Görünümü eşitlemeyi zamanla|**CTRL + \\ , CTRL + aşağı ok**| Diff.SynchronizeViewToggle |
|Açıklama Ekle|**Ctrl+Shift+K**| EditorContextMenus.CodeWindow.AddComment |
|Yerel dosyayı Düzenle|**CTRL + SHIFT + P**| EditorContextMenus.CodeWindow.EditLocalFile |

### <a name="dom-explorer-context-specific-shortcuts"></a><a name="bkmk_dom-explorer-context-specific-shortcuts"></a> DOM Gezgini: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Yenile|**F5**| DOMExplorer.Refresh |
|Öğe seçme|**Ctrl+B**| DOMExplorer.SelectElement |
|Düzeni göster|**Ctrl+Shift+I**| DOMExplorer.ShowLayout |

### <a name="f-interactive-context-specific-shortcuts"></a><a name="bkmk_f-interactive-context-specific-shortcuts"></a> F# Etkileşimli: Bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Etkileşimli değerlendirmeyi iptal etme|**Ctrl+Break tuşu**| OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation |

### <a name="graph-document-editor-context-specific-shortcuts"></a><a name="bkmk_graph-document-editor-context-specific-shortcuts"></a>Graph Belge Düzenleyicisi: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Düğüm ekleme|**Ekle**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode |
|Her iki bağımlılık da|**B**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies |
|Gelen bağımlılıklar|**I**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies |
|Giden bağımlılıklar|**O**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies |
|Yeni açıklama|**Ctrl+Shift+K**<br /><br /> veya<br /><br /> **Ctrl+E, C**| ArchitectureContextMenus.DirectedGraphContextMenu.NewComment |
|Kaldır|**Silme**| ArchitectureContextMenus.DirectedGraphContextMenu.Remove |
|Rename|**F2**| ArchitectureContextMenus.DirectedGraphContextMenu.Rename |

### <a name="graphics-diagnostics-context-specific-shortcuts"></a><a name="bkmk_graphics-diagnostics-context-specific-shortcuts"></a> Grafik Tanılama: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Yakalama çerçevesi|Hiçbiri| Debug.Graphics.CaptureFrame |
|Piksel seçimini aşağı taşı|**Shift+Alt+Aşağı Ok**| Graphics.MovePixelSelectionDown |
|Piksel seçimini sola taşı|**Shift+Alt+Sol Ok**| Graphics.MovePixelSelectionLeft |
|Piksel seçimini sağa taşıma|**Shift+Alt+Sağ Ok**| Graphics.MovePixelSelectionRight |
|Piksel seçimini yukarı taşı|**Shift+Alt+Yukarı Ok**| Graphics.MovePixelSelectionUp |
|Gerçek boyuta yakınlaştırma|**Shift+Alt+0** (sıfır)| Graphics.ZoomToActualSize |
|Pencereye sığdırmak için yakınlaştır|**Shift+Alt+9**| Graphics.ZoomToFitInWindow |
|Yakınlaştır|**Shift+Alt+=**| Graphics.ZoomIn |
|Uzaklaştır|**Shift+Alt+-**| Graphics.ZoomOut |

### <a name="html-editor-context-specific-shortcuts"></a><a name="bkmk_html-editor-context-specific-shortcuts"></a> HTML Düzenleyicisi: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Denetleyiciye gidin|**Ctrl+M, Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |

### <a name="html-editor-design-view-context-specific-shortcuts"></a><a name="bkmk_html-editor-design-view-context-specific-shortcuts"></a> HTML Düzenleyicisi Tasarım Görünümü: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Denetimi aşağı taşıma|**Ctrl+Aşağı Ok**| Edit.MoveControlDown |
|Denetimi yukarı taşıma|**Ctrl+Yukarı Ok**| Edit.MoveControlUp |
|Kalın|**Ctrl+B**| Format.Bold |
|Köprüye dönüştürme|**Ctrl+L**| Format.ConverttoHyperlink |
|Yer işareti ekleme|**Ctrl+Shift+L**| Format.InsertBookmark |
|İtalik|**Ctrl+I**| Format.Italic |
|Altçizgi|**Ctrl+U**| Format.Underline |
|İçerik ekleme sayfası|**Ctrl+M, Ctrl+C**| Project.AddContentPage |
|Soldaki sütun|**Ctrl+Alt+Sol Ok**| Table.ColumntotheLeft |
|Sütunun sağına|**Ctrl+Alt+Sağ Ok**| Table.ColumntotheRight |
|Yukarıdaki satır|**Ctrl+Alt+Yukarı Ok**| Table.RowAbove |
|Aşağıdaki satır|**Ctrl+Alt+Aşağı Ok**| Table.RowBelow |
|NET nongörsel olmayan denetimler|**Ctrl+Shift+N**| View.ASP.NETNonvisualControls |
|Ana Şablonu Düzenle|**Ctrl+M, Ctrl+M**| View.EditMaster |
|Sonraki görünüm|**Ctrl+PgDn**| View.NextView |
|Akıllı etiketi göster|**Shift+Alt+F10**| View.ShowSmartTag |
|İşaretlemeyi görüntüle|**Shift+F7**| View.ViewMarkup |
|Önceki sekme|**Ctrl+PgUp**| Window.PreviousTab |

### <a name="html-editor-source-view-context-specific-shortcuts"></a><a name="bkmk_html-editor-source-view-context-specific-shortcuts"></a> HTML düzenleyici kaynak görünümü: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Denetleyiciye git|**Ctrl+M, Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |
|Sonraki görünüm|**Ctrl+PgDn**| View.NextView |
|Görünümleri eşitler|**Ctrl+Shift+Y**| View.SynchronizeViews |
|Görünüm tasarımcısı|**Shift+F7**| View.ViewDesigner |
|Önceki sekme|**Ctrl+PgUp**| Window.PreviousTab |

### <a name="layer-diagram-context-specific-shortcuts"></a><a name="bkmk_layer-diagram-context-specific-shortcuts"></a> Katman diyagramı: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komut|Klavye kısayolu|Komut KIMLIĞI|
|-|-|-|
|Sil|**Shift+Delete**| Edit.Delete |

### <a name="managed-resources-editor-context-specific-shortcuts"></a><a name="bkmk_managed-resources-editor-context-specific-shortcuts"></a> Yönetilen kaynaklar Düzenleyicisi: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Hücreyi Düzenle|**F2**| Edit.EditCell |
|Kaldır|**Silme**| Edit.Remove |
|Satırı Kaldır|**Ctrl+Delete**| Edit.RemoveRow |
|Seçimi iptal et|**Esc**| Edit.SelectionCancel |
|Ses|**Ctrl+4**| Resources.Audio |
|Dosyalar|**Ctrl+5**| Resources.Files |
|Simgeler|**Ctrl+3**| Resources.Icons |
|Görüntüler|**Ctrl+2**| Resources.Images |
|Diğer|**Ctrl+6**| Resources.Other |
|Dizeler|**CTRL + 1**| Resources.Strings |

### <a name="merge-editor-window-context-specific-shortcuts"></a><a name="bkmk_merge-editor-window-context-specific-shortcuts"></a> Düzenleyici penceresini birleştir: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Sol pencereye odaklanmak için ayarla|**Alt+1**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow |
|Sonuç penceresinde odağı ayarla|**Alt+2**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow |
|Sağ pencereye odaklanmak için ayarla|**Alt+3**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow |

### <a name="microsoft-sql-server-data-tools-schema-compare-context-specific-shortcuts"></a><a name="bkmk_microsoft-sql-server-data-tools-schema-compare-context-specific-shortcuts"></a>Microsoft SQL Server Veri araçları, şema karşılaştırması: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|SSDT şeması karşılaştırma karşılaştırması|**Shift+Alt+C**| SQL.SSDTSchemaCompareCompare |
|SSDT şema karşılaştırma betiği oluştur|**Shift+Alt+G**| SQL.SSDTSchemaCompareGenerateScript |
|SSDT şeması karşılaştırma sonraki değişiklik|**SHIFT + alt +.**| SQL.SSDTSchemaCompareNextChange |
|SSDT şeması önceki değişikliği Karşılaştır|**SHIFT + alt +,**| SQL.SSDTSchemaComparePreviousChange |
|SSDT şema karşılaştırması durdur|**Alt+Break**| SQL.SSDTSchemaCompareStop |
|SSDT şeması karşılaştırma yazma güncelleştirmeleri|**Shift+Alt+U**| SQL.SSDTSchemaCompareWriteUpdates |

### <a name="microsoft-sql-server-data-tools-table-designer-context-specific-shortcuts"></a><a name="bkmk_microsoft-sql-server-data-tools-table-designer-context-specific-shortcuts"></a>Microsoft SQL Server Veri araçları, Tablo Tasarımcısı: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|CommitAllEdits|**Shift+Alt+U**|
|Joker karakterleri Genişlet|**Ctrl+R, E**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|Adları tam olarak nitelendir|**Ctrl+R, Q**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Şemaya taşı|**Ctrl+R, M**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|Rename|**F2**<br /><br /> veya<br /><br /> **Ctrl+R, R**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|ViewFileInScriptPanel|**Shift+Alt+PgDn**| |

### <a name="microsoft-sql-server-data-tools-t-sql-editor-context-specific-shortcuts"></a><a name="bkmk_microsoft-sql-server-data-tools-t-sql-editor-context-specific-shortcuts"></a>Microsoft SQL Server veri araçları, T-SQL düzenleyicisi: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|CommitAllEdits|**Shift+Alt+U**|
|Hata ayıklayıcı ile Yürüt|**Alt+F5**| SQL.ExecuteWithDebugger |
|Joker karakterleri Genişlet|**Ctrl+R, E**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|Adları tam olarak nitelendir|**Ctrl+R, Q**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Şemaya taşı|**Ctrl+R, M**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|Rename|**F2**<br /><br /> veya<br /><br /> **Ctrl+R, R**<br /><br /> veya<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|T SQL düzenleyicisi sorguyu iptal et|**Alt+Break**| SQL.TSqlEditorCancelQuery |
|T SQL düzenleyicisi sorgu yürütme|**Ctrl+Shift+E**| SQL.TSqlEditorExecuteQuery |
|dosya olarak SQL düzenleyici sonuçları|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|düzenleyici sonuçlarını kılavuz olarak SQL|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|SQL düzenleyici sonuçları metin olarak|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|T SQL düzenleyicisi tahmini planı göster|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|T SQL düzenleyicisi yürütme planını değiştirme|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|T SQL düzenleyicisi geçiş sonuçları bölmesi|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|T SQL düzenleyicisi kopya sorgusu|**Ctrl+Alt+N**|SQL. Tsqtaditorclonequery |
|T SQL düzenleyicisi veritabanı birleşik kutusu|**Shift+Alt+PgDn**|SQL. Tsqtaditordatabasecombo |

### <a name="microsoft-sql-server-data-tools-t-sql-pdw-editor-context-specific-shortcuts"></a><a name="bkmk_microsoft-sql-server-data-tools-t-sql-pdw-editor-context-specific-shortcuts"></a>Microsoft SQL Server veri araçları, T-SQL PDW düzenleyicisi: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|T SQL düzenleyicisi sorguyu iptal et|**Alt+Break**| SQL.TSqlEditorCancelQuery |
|T SQL düzenleyicisi sorgu yürütme|**Ctrl+Shift+E**| SQL.TSqlEditorExecuteQuery |
|dosya olarak SQL düzenleyici sonuçları|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|düzenleyici sonuçlarını kılavuz olarak SQL|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|SQL düzenleyici sonuçları metin olarak|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|T SQL düzenleyicisi tahmini planı göster|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|T SQL düzenleyicisi yürütme planını değiştirme|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|T SQL düzenleyicisi geçiş sonuçları bölmesi|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|T SQL düzenleyicisi kopya sorgusu|**Ctrl+Alt+N**|SQL. Tsqtaditorclonequery |
|T SQL düzenleyicisi kopya sorgusu|**Shift+Alt+PgDn**|SQL. Tsqtaditorclonequery |

### <a name="page-inspector-context-specific-shortcuts"></a><a name="bkmk_page-inspector-context-specific-shortcuts"></a> Sayfa denetçisi: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komut|Klavye kısayolu|Komut KIMLIĞI|
|-|-|-|
|Simge durumuna küçült|**F12**| PageInspector.Minimize |

### <a name="query-designer-context-specific-shortcuts"></a><a name="bkmk_query-designer-context-specific-shortcuts"></a> Sorgu Tasarımcısı: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Veri almayı iptal et|**CTRL + T**| QueryDesigner.CancelRetrievingData |
|Ölçütler|**Ctrl+2**| QueryDesigner.Criteria |
|Diyagram|**CTRL + 1**| QueryDesigner.Diagram |
|SQL Yürüt|**Ctrl+R**| QueryDesigner.ExecuteSQL |
|Satıra git|**Ctrl+G**| QueryDesigner.GotoRow |
|JOIN modu|**Ctrl+Shift+J**| QueryDesigner.JoinMode |
|Sonuçlar|**Ctrl+4**| QueryDesigner.Results |
|Sql|**Ctrl+3**| QueryDesigner.SQL |

### <a name="query-results-context-specific-shortcuts"></a><a name="bkmk_query-results-context-specific-shortcuts"></a> Sorgu sonuçları: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Sorgu sonuçları yeni satırı|**Alt+End**| SQL.QueryResultsNewRow |
|Sorgu sonuçlarını yenileme|**Shift+Alt+R**| SQL.QueryResultsRefresh |
|Sorgu sonuçları durdurma|**Alt+Break**| SQL.QueryResultsStop |

### <a name="report-designer-context-specific-shortcuts"></a><a name="bkmk_report-designer-context-specific-shortcuts"></a> Rapor Tasarımcısı: Bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Kesme çizgisi|**Enter**| Edit.BreakLine |
|Char sol|**Sol Ok**| Edit.CharLeft |
|Char sol genişletme|**Shift+Sol Ok**| Edit.CharLeftExtend |
|Char right|**Sağ Ok**| Edit.CharRight |
|Karakter sağ genişletme|**Shift+Sağ Ok**| Edit.CharRightExtend |
|Ekle sekmesi|**Sekme**| Edit.InsertTab |
|Satır aşağı|**Aşağı Ok**| Edit.LineDown |
|Çizgi aşağı genişletme|**Shift+Aşağı Ok**| Edit.LineDownExtend |
|Sırala|**Yukarı Ok**| Edit.LineUp |
|Genişletmeyi yukarı doğru sırala|**Shift+Yukarı Ok**| Edit.LineUpExtend |
|Denetimi aşağı taşıma|**Ctrl+Aşağı Ok**| Edit.MoveControlDown |
|Denetimi sola taşıma|**Ctrl+Sol Ok**| Edit.MoveControlLeft |
|Denetimi sağa taşıma|**Ctrl+Sağ Ok**| Edit.MoveControlRight |
|Denetimi yukarı taşıma|**Ctrl+Yukarı Ok**| Edit.MoveControlUp |
|Seçim iptali|**Esc**| Edit.SelectionCancel |
|Boyut denetimi aşağı|**Ctrl+Shift+Aşağı Ok**| Edit.SizeControlDown |
|Boyut denetimi sola|**Ctrl+Shift+Sol Ok**| Edit.SizeControlLeft |
|Boyut denetimi hakkı|**Ctrl+Shift+Sağ Ok**| Edit.SizeControlRight |
|Boyut denetimi|**Ctrl+Shift+Yukarı Ok**| Edit.SizeControlUp |
|Sekme sol|**Shift+Sekme Tuşu**| Edit.TabLeft |
| Rapor verileri|**Ctrl+Alt+D**| View.ReportData |

### <a name="sequence-diagram-context-specific-shortcuts"></a><a name="bkmk_sequence-diagram-context-specific-shortcuts"></a> Sıralı diyagram: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Koda gidin|**F12**| ArchitectureDesigner.Sequence.NavigateToCode |
|Sil|**Shift+Del**| Edit.Delete |

### <a name="settings-designer-context-specific-shortcuts"></a><a name="bkmk_settings-designer-context-specific-shortcuts"></a>Ayarlar Tasarımcı: bağlama özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Hücreyi Düzenle|**F2**| Edit.EditCell |
|Satırı Kaldır|**Ctrl+Delete**| Edit.RemoveRow |
|Seçimi iptal et|**Esc**| Edit.SelectionCancel |
|Kodu görüntüle|**F7**| View.ViewCode |

### <a name="solution-explorer-context-specific-shortcuts"></a><a name="bkmk_solution-explorer-context-specific-shortcuts"></a> Çözüm Gezgini: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komut|Klavye kısayolu|Komut KIMLIĞI|
|-|-|-|
|Sayfa denetçisinde görüntüle|**Ctrl+K, Ctrl+G**| ClassViewContextMenus.ClassViewProject.View.ViewinPageInspector |

### <a name="team-explorer-context-specific-shortcuts"></a><a name="bkmk_team-explorer-context-specific-shortcuts"></a> Takım Gezgini: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komut|Klavye Kısayolu|Komut KIMLIĞI|
|-|-|-|
|Sil|**Silme**| Edit.Delete |
|Rename|**F2**| File.Rename |
|Takım Gezgini gezintisine git|**Alt+Home**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNavigation |
|Takım Gezgini sonraki bölüm içeriğine git|**Alt+Aşağı Ok**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNextSectionContent |
|Takım Gezgini sayfa içeriğine git|**Alt + 0** (sıfır)| TeamFoundationContextMenus.Commands.GoToTeamExplorerPageContent |
|Takım Gezgini önceki bölüm içeriğine git|**Alt+Yukarı Ok**| TeamFoundationContextMenus.Commands.GoToTeamExplorerPreviousSectionContent |
|Takım Gezgini Bölüm 1 içeriğine git|**Alt+1**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection1Content |
|Takım Gezgini Bölüm 2 içeriğine git|**Alt+2**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection2Content |
|Takım Gezgini Bölüm 3 içeriğine git|**Alt+3**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection3Content |
|Takım Gezgini Bölüm 4 içeriğine git|**Alt+4**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection4Content |
|Takım Gezgini Bölüm 5 içeriğine git|**Alt+5**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection5Content |
|Takım Gezgini Bölüm 6 içeriğine git|**Alt+6**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection6Content |
|Takım Gezgini Bölüm 7 içeriğine git|**Alt+7**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content |
|Takım Gezgini Bölüm 8 içeriğine git|**Alt+8**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content |
|Takım Gezgini Bölüm 9 içeriğine git|**Alt+9**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content |
|Takım Gezgini geriye git|**Alt+Sol Ok**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward |
|Takım Gezgini ileri git|**Alt+Sağ Ok**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward |
|TFS bağlamı My İş Sayfam Wi-Kopyala oluştur|**Shift+Alt+C**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI |
|TFS bağlamı iş sayfam yeni bağlantılı Wi|**Shift+Alt+L**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI |
|Yenile|**F5**| View.Refresh |

### <a name="test-explorer-context-specific-shortcuts"></a><a name="bkmk_test-explorer-context-specific-shortcuts"></a> Test Gezgini: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komut|Klavye kısayolu|Komut KIMLIĞI|
|-|-|-|
|Testi aç|**F12**| TestExplorer.OpenTest |

### <a name="text-editor-context-specific-shortcuts"></a><a name="bkmk_text-editor-context-specific-shortcuts"></a> Metin düzenleyici: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


| Komutlar | Klavye kısayolları |Komut KIMLIĞI|
|-|-|-|
|Çizgiyi Böl| **Enter**<br /><br /> veya<br /><br /> **Shift+Enter** | Edit.BreakLine |
|Sol karakter| **Sol Ok** | Edit.CharLeft |
|Karakter sola Genişlet| **Shift+Sol Ok** | Edit.CharLeftExtend |
|Karakter sola Genişlet sütunu| **Shift+Alt+Sol Ok** | Edit.CharLeftExtendColumn |
|Sağ karakter| **Sağ Ok** | Edit.CharRight |
|Sağ karakter Genişlet| **Shift+Sağ Ok** | Edit.CharRightExtend |
|Karakter sağ Genişlet sütunu| **Shift+Alt+Sağ Ok** | Edit.CharRightExtendColumn |
|Yer imlerini temizle| **Ctrl+K, Ctrl+L** | Edit.ClearBookmarks |
|Tüm anahat oluşturmayı Daralt| **Ctrl+M, Ctrl+A** | Edit.CollapseAllOutlining |
|Geçerli bölgeyi Daralt| **Ctrl+M, Ctrl+S** | Edit.CollapseCurrentRegion |
|Etiketi Daralt| **Ctrl+M, Ctrl+T** | Edit.CollapseTag |
|Tanımlara Daralt| **CTRL + M, CTRL + O** (harf ' O ') | Düzenle. CollapseToDefinitions |
|Sözleşme seçimi| **SHIFT + alt +-** | . ContractSelection öğesini Düzenle |
|Açıklama seçimi| **Ctrl+K, Ctrl+C** | Edit.CommentSelection |
|Sözcüğü Tamam| **Ctrl+Ara Çubuğu**<br /><br /> veya<br /><br /> **Alt+Sağ Ok** | Edit.CompleteWord |
|Parametre ipucunu Kopyala| **Ctrl+Shift+Alt+C** | Edit.CopyParameterTip |
|Filtre düzeyini azalt| **Alt+,** | Edit.DecreaseFilterLevel |
|Geriye doğru Sil| **Geri Al tuşu**<br /><br /> veya<br /><br /> **Shift+Geri Al tuşu** | Edit.DeleteBackwards |
|Yatay boşluğu Sil| **CTRL + K, CTRL +\\** | Edit.DeleteHorizontalWhiteSpace |
|Belge sonu| **Ctrl+End** | Edit.DocumentEnd |
|Belge bitişi uzat| **Ctrl+Shift+End** | Edit.DocumentEndExtend |
|Belge başlangıcı| **Ctrl+Home** | Edit.DocumentStart |
|Belge başlangıcını uzat| **Ctrl+Shift+Home** | Edit.DocumentStartExtend |
|Tüm anahat oluşturmayı Genişlet| **Ctrl+M, Ctrl+X** | Edit.ExpandAllOutlining |
|Geçerli bölgeyi Genişlet| **Ctrl+M, Ctrl+E** | Edit.ExpandCurrentRegion |
|Seçimi genişlet| **SHIFT + alt + =** | . ExpandSelection öğesini Düzenle |
|Seçimi kapsayan bloğa Genişlet| **SHIFT + alt +]** | . ExpandSelectiontoContainingBlock öğesini Düzenle |
|Belgeyi biçimlendir| **Ctrl+K, Ctrl+D** | Edit.FormatDocument |
|Biçim seçimi| **Ctrl+K, Ctrl+F** | Edit.FormatSelection |
|Tümüne git| **CTRL + T**<br /><br /> veya<br /><br /> **CTRL +,** | . Sayfayall Düzenle |
|Küme ayracı| **Ctrl+]** | Edit.GotoBrace |
|Küme ayracı genişletme| **Ctrl+Shift+]** | Edit.GotoBraceExtend |
|Son zamanlarda yapılanlar| **Ctrl+T,R** | Edit.GotoRecent |
|Dosyada bir sonraki soruna var| **Alt+PgDn** | Edit.GotoNextIssueinFile |
|Dosyada önceki soruna var| **Alt+PgUp** | Edit.GotoPreviousIssueinFile |
|Seçimi gizle| **Ctrl+M, Ctrl+H** | Edit.HideSelection |
|Filtre düzeyini artırma| **Alt+.** | Edit.IncreaseFilterLevel |
|Artımlı arama| **Ctrl+I** | Edit.IncrementalSearch |
|Eşleştirmeye hiç caret ekleme| **Shift+Alt+;** | Edit.InsertCaretsatAllMatching |
|Sonraki eşleşen imtiyazı ekle| **Shift+Alt+.** | Edit.InsertNextMatchingCaret |
|Ekle sekmesi| **Sekme** | Edit.InsertTab |
|Satır kesme| **Ctrl+L** | Edit.LineCut |
|Satır silme| **Ctrl+Shift+L** | Edit.LineDelete |
|Satır aşağı| **Aşağı Ok** | Edit.LineDown |
|Çizgi aşağı genişletme| **Shift+Aşağı Ok** | Edit.LineDownExtend |
|Satır aşağı genişletme sütunu| **Shift+Alt+Aşağı Ok** | Edit.LineDownExtendColumn |
|Satır sonu| **End** | Edit.LineEnd |
|Satır sonu genişletme| **Shift+End** | Edit.LineEndExtend |
|Satır sonu genişletme sütunu| **Shift+Alt+End** | Edit.LineEndExtendColumn |
|Yukarıda açık satır| **Ctrl+Enter** | Edit.LineOpenAbove |
|Satır aşağıda açık| **Ctrl+Shift+Enter** | Edit.LineOpenBelow |
|Satır başlangıcı| **Giriş Ekranı** | Edit.LineStart |
|Satır başlangıcı genişletme| **Shift+Home** | Edit.LineStartExtend |
|Satır başlangıcı sütunu genişletme| **Shift+Alt+Home** | Edit.LineStartExtendColumn |
|Satır sıraları| **Shift+Alt+T** | Edit.LineTranspose |
|Sırala| **Yukarı Ok** | Edit.LineUp |
|Genişletmeyi yukarı doğru sırala| **Shift+Yukarı Ok** | Edit.LineUpExtend |
|Sütunu yukarı doğru genişletme| **Shift+Alt+Yukarı Ok** | Edit.LineUpExtendColumn |
|Üyeleri listele| **Ctrl+J** | Edit.ListMembers |
|Küçük harfli yapma| **Ctrl+U** | Edit.MakeLowercase |
|Büyük harfli yapma| **Ctrl+Shift+U** | Edit.MakeUppercase |
|Seçili satırları aşağı taşıma| **Alt+Aşağı Ok** | Edit.MoveSelectedLinesDown |
|Seçili satırları yukarı taşıma| **Alt+Yukarı Ok** | Edit.MoveSelectedLinesUp |
|Sonraki vurgulanan başvuru| **Ctrl+Shift+Aşağı Ok** | Edit.NextHighlightedReference |
|Üzerine yazma modu| **Ekle** | Edit.OvertypeMode |
|Sayfa aşağı| **PgDn** | Edit.PageDown |
|Sayfa aşağı genişlet| **Shift+PgDn** | Edit.PageDownExtend |
|Sayfa yukarı| **PgUp** | Edit.PageUp |
|Sayfa yukarı Genişlet| **Shift+PgUp** | Edit.PageUpExtend |
|Parametre bilgisi| **Ctrl+Shift+Ara Çubuğu** | Edit.ParameterInfo |
|Parametre ipucunu Yapıştır| **Ctrl+Shift+Alt+P** | Edit.PasteParameterTip |
|Geriye göz at| **Ctrl+Alt+-** | Edit.PeekBackward |
|Açıklama Özeti| **Alt+F12** | Edit.PeekDefinition |
|İleriye göz at| **Ctrl + alt + =** | Edit.PeekForward |
|Önceki vurgulanan başvuru| **Ctrl+Shift+Yukarı Ok** | Edit.PreviousHighlightedReference |
|Hızlı bilgi| **Ctrl+K, Ctrl+I** | Edit.QuickInfo |
|Ters Artımlı arama| **Ctrl+Shift+I** | Edit.ReverseIncrementalSearch |
|Satırı aşağı kaydır| **Ctrl+Aşağı Ok** | Edit.ScrollLineDown |
|Bir satır yukarı kaydır| **Ctrl+Yukarı Ok** | Edit.ScrollLineUp |
|Geçerli sözcüğü seç| **Ctrl+W** | Edit.SelectCurrentWord |
|Seçimi iptal et| **Esc** | Edit.SelectionCancel |
|En son geri dönmek için seçin| **CTRL + =** | Edit.SelectToLastGoBack |
|Kod lens menüsünü göster| **CTRL + K, CTRL +\`** | Edit.ShowCodeLensMenu |
|Git menüsünü göster| **Alt +\`** | Edit. ShowNavigateMenu |
|Geçerli gizlemeyi durdur| **Ctrl+M, Ctrl+U** | Edit.StopHidingCurrent |
|Anahat oluşturmayı durdur| **Ctrl+M, Ctrl+P** | Edit.StopOutlining |
|Geçişi Değiştir| **Ctrl+K, Ctrl+A** | Edit.SwapAnchor |
|Sekme sola| **Shift+Sekme Tuşu** | Edit.TabLeft |
|Tüm anahatlamayı aç| **Ctrl+M, Ctrl+L** | Edit.ToggleAllOutlining |
|Yer işaretini değiştirme| **Ctrl+K, Ctrl+K** | Edit.ToggleBookmark |
|Tamamlama modunu aç| **Ctrl+Alt+Ara Çubuğu** | Edit.ToggleCompletionMode |
|Anahat genişletmeyi değiştirme| **Ctrl+M, Ctrl+M** | Edit.ToggleOutliningExpansion |
|Görev listesi kısayolunu değiştirme| **Ctrl+K, Ctrl+H** | Edit.ToggleTaskListShortcut |
|Sözcük kaydırmayı aç| **Ctrl+E, Ctrl+W** | Edit.ToggleWordWrap |
|Seçimi açıklama kaldır| **Ctrl+K, Ctrl+U** | Edit.UncommentSelection |
|En Alta görüntüle| **Ctrl+PgDn** | Edit.ViewBottom |
|Alt genişletmeyi görüntüle| **Ctrl+Shift+PgDn** | Edit.ViewBottomExtend |
|Üst görünümü| **Ctrl+PgUp** | Edit.ViewTop |
|Üst genişletmeyi görüntüle| **Ctrl+Shift+PgUp** | Edit.ViewTopExtend |
|Boşluğu görüntüleme| **Ctrl+R, Ctrl+W** | Edit.ViewWhiteSpace |
|Sona kadar sözcük silme| **Ctrl+Delete** | Edit.WordDeleteToEnd |
|Başlamak için sözcük silme| **Ctrl+Geri Al tuşu** | Edit.WordDeleteToStart |
|Sonraki sözcük| **Ctrl+Sağ Ok** | Edit.WordNext |
|Word next extend| **Ctrl+Shift+Sağ Ok** | Edit.WordNextExtend |
|Word next extend column| **Ctrl+Shift+Alt+Sağ Ok** | Edit.WordNextExtendColumn |
|Önceki sözcük| **Ctrl+Sol Ok** | Edit.WordPrevious |
|Word önceki genişletme| **Ctrl+Shift+Sol Ok** | Edit.WordPreviousExtend |
|Word önceki genişletme sütunu| **Ctrl+Shift+Alt+Sol Ok** | Edit.WordPreviousExtendColumn |
|Sözcük dönüşüm| **Ctrl+Shift+T** | Edit.WordTranspose |
|Etkileşimli olarak yürütme| **Alt+Enter** | EditorContextMenus.CodeWindow.ExecuteInInteractive |
|Satırı etkileşimli olarak yürütme| **Alt+'** | EditorContextMenus.CodeWindow.ExecuteLineInInteractive |
|Sayfa denetçisinde görüntüle| **Ctrl+K, Ctrl+G** | OtherContextMenus.HTMLContext.ViewinPageInspector |
|TFS sonraki bölgeye taşıma ek açıklama ekleme| **Alt+PgDn** | TeamFoundationContextMenus.Annotate.TfsAnnotateMoveNextRegion |
|TFS önceki bölgeyi taşımaya açıklama ekleme| **Alt+PgUp** | TeamFoundationContextMenus.Annotate.TfsAnnotateMovePreviousRegion |

### <a name="uml-activity-diagram-context-specific-shortcuts"></a><a name="bkmk_uml-activity-diagram-context-specific-shortcuts"></a> UML etkinlik diyagramı: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Sil|**Shift+Del**| Edit.Delete |

### <a name="uml-class-diagram-context-specific-shortcuts"></a><a name="bkmk_uml-class-diagram-context-specific-shortcuts"></a> UML sınıf diyagramı: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Modelden sil|**Shift+Del**| Edit.DeleteFromModel |

### <a name="uml-component-diagram-context-specific-shortcuts"></a><a name="bkmk_uml-component-diagram-context-specific-shortcuts"></a> UML bileşen diyagramı: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Modelden sil|**Shift+Del**| Edit.DeleteFromModel |

### <a name="uml-use-case-diagram-context-specific-shortcuts"></a><a name="bkmk_uml-use-case-diagram-context-specific-shortcuts"></a> UML kullanım durumu diyagramı: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komut|Klavye kısayolu|Komut Kimliği|
|-|-|-|
|Modelden sil|**Shift+Del**| Edit.DeleteFromModel |

### <a name="vc-accelerator-editor-context-specific-shortcuts"></a><a name="bkmk_vc-accelerator-editor-context-specific-shortcuts"></a> VC Hızlandırıcı düzenleyicisi: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Yeni hızlandırıcı|**Ekle**| Edit.NewAccelerator |
|Sonraki anahtar türü|**Ctrl+W**| Edit.NextKeyTyped |

### <a name="vc-dialog-editor-context-specific-shortcuts"></a><a name="bkmk_vc-dialog-editor-context-specific-shortcuts"></a> VC İletişim Kutusu Düzenleyicisi: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Denetimi aşağı taşıma|**Aşağı Ok**| Edit.MoveControlDown |
|Denetimi sola taşıma|**Sol Ok**| Edit.MoveControlLeft |
|Denetimi sağa taşıma|**Sağ Ok**| Edit.MoveControlRight |
|Denetimi yukarı taşıma|**Yukarı Ok**| Edit.MoveControlUp |
|Sütunu sola kaydırma|**Ctrl+Sol Ok**| Edit.ScrollColumnLeft |
|Sütunu sağa kaydırma|**Ctrl+Sağ Ok**| Edit.ScrollColumnRight |
|Satırı aşağı kaydırma|**Ctrl+Aşağı Ok**| Edit.ScrollLineDown |
|Yukarı doğru kaydırma|**Ctrl+Yukarı Ok**| Edit.ScrollLineUp |
|Boyut denetimi aşağı|**Shift+Aşağı Ok**| Edit.SizeControlDown |
|Boyut denetimi sola|**Shift+Sol Ok**| Edit.SizeControlLeft |
|Boyut denetimi hakkı|**Shift+Sağ Ok**| Edit.SizeControlRight |
|Boyut denetimi|**Shift+Yukarı Ok**| Edit.SizeControlUp |
|Altları hizala|**Ctrl+Shift+Aşağı Ok**| Format.AlignBottoms |
|Merkezleri hizalama|**Shift+F9**| Format.AlignCenters |
|Sola hizala|**Ctrl+Shift+Sol Ok**| Format.AlignLefts |
|Ortaları hizala|**F9**| Format.AlignMiddles |
|Hakları hizalama|**Ctrl+Shift+Sağ Ok**| Format.AlignRights |
|Üstleri hizala|**Ctrl+Shift+Yukarı Ok**| Format.AlignTops |
|Alttaki düğme|**Ctrl+B**| Format.ButtonBottom |
|Sağ düğme|**Ctrl+R**| Format.ButtonRight |
|Orta yatay|**Ctrl+Shift+F9**| Format.CenterHorizontal |
|Orta dikey|**Ctrl+F9**| Format.CenterVertical |
|Mnemonics'i denetleme|**Ctrl+M**| Format.CheckMnemonics |
|İçerik boyutu|**Shift+F7**| Format.SizetoContent |
|Boşluk genelinde|**Alt+Sağ Ok**<br /><br /> veya<br /><br /> **Alt+Sol Ok**| Format.SpaceAcross |
|Boşluk aşağı|**Alt+Yukarı Ok**<br /><br /> veya<br /><br /> **Alt+Aşağı Ok**| Format.SpaceDown |
|Sekme sırası|**Ctrl+D**| Format.TabOrder |
|Test iletişim kutusu|**Ctrl+T**| Format.TestDialog |
|Geçiş kılavuzları|**Ctrl+G**| Format.ToggleGuides |

### <a name="vc-image-editor-context-specific-shortcuts"></a><a name="bkmk_vc-image-editor-context-specific-shortcuts"></a> VC Görüntü Düzenleyicisi: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Airbrush aracı|**Ctrl+A**| Image.AirbrushTool |
|Fırça aracı|**Ctrl+B**| Image.BrushTool |
|Kopyalama ve ana hat seçimi|**Ctrl+Shift+U**| Image.CopyandOutlineSelection |
|Opak çizme|**Ctrl+J**| Image.DrawOpaque |
|Üç nokta aracı|**Alt+P**| Image.EllipseTool |
|Silme aracı|**Ctrl+Shift+I**| Image.EraseTool |
|Doldurulmuş üç nokta aracı|**Ctrl+Shift+Alt+P**| Image.FilledEllipseTool |
|Doldurulmuş dikdörtgen aracı|**Ctrl+Shift+Alt+R**| Image.FilledRectangleTool |
|Doldurulmuş yuvarlanmış dikdörtgen aracı|**Ctrl+Shift+Alt+W**| Image.FilledRoundedRectangleTool |
|Dolgu aracı|**Ctrl+F**| Image.FillTool |
|Yatay çevirme|**Ctrl+H**| Image.FlipHorizontal |
|Dikey çevirme|**Shift+Alt+H**| Image.FlipVertical |
|Daha büyük fırça|**Ctrl+=**| Image.LargerBrush |
|Çizgi aracı|**Ctrl+L**| Image.LineTool |
|Büyütme aracı|**Ctrl+M**| Image.MagnificationTool |
|Büyütmek|**Ctrl+Shift+M**| Image.Magnify |
|Yeni görüntü türü|**Ekle**| Image.NewImageType |
|Sonraki renk|**Ctrl+]**<br /><br /> veya<br /><br /> **Ctrl+Sağ Ok**| Image.NextColor |
|Sağ sonraki renk|**Ctrl+Shift+]**<br /><br /> veya<br /><br /> **Ctrl+Shift+Sağ Ok**| Image.NextRightColor |
|Özetlenen üç nokta aracı|**Shift+Alt+P**| Image.OutlinedEllipseTool |
|Özetlenen dikdörtgen aracı|**Shift+Alt+R**| Image.OutlinedRectangleTool |
|Özetlenen yuvarlanmış dikdörtgen araç|**Shift+Alt+W**| Image.OutlinedRoundedRectangleTool |
|Kalem aracı|**Ctrl+I**| Image.PencilTool |
|Önceki renk|**Ctrl+[**<br /><br /> veya<br /><br /> **Ctrl+Sol Ok**| Image.PreviousColor |
|Önceki sağ renk|**Ctrl+Shift+[**<br /><br /> veya<br /><br /> **Ctrl+Shift+Sol Ok**| Image.PreviousRightColor |
|Dikdörtgen seçim aracı|**Shift+Alt+S**| Image.RectangleSelectionTool |
|Dikdörtgen araç|**Alt+R**| Image.RectangleTool |
|90 Derece Döndür derece|**Ctrl+Shift+H**| Image.Rotate90Degrees |
|Yuvarlanmış dikdörtgen araç|**Alt+W**| Image.RoundedRectangleTool |
|Kılavuzu göster|**Ctrl+Alt+S**| Image.ShowGrid |
|Kutucuk kılavuzu göster|**Ctrl+Shift+Alt+S**| Image.ShowTileGrid |
|Küçük fırça|**Ctrl+.**| Image.SmallBrush |
|Daha küçük fırça|**CTRL +-**| Image.SmallerBrush |
|Metin aracı|**CTRL + T**| Image.TextTool |
|Seçimi fırça olarak kullan|**Ctrl+U**| Image.UseSelectionasBrush |
|Yakınlaştır|**CTRL + SHIFT +.**<br /><br /> veya<br /><br /> **Ctrl+Yukarı Ok**| Image.ZoomIn |
|Uzaklaştır|**CTRL + SHIFT +,**<br /><br /> veya<br /><br /> **Ctrl+Aşağı Ok**| Image.ZoomOut |

### <a name="vc-string-editor-context-specific-shortcuts"></a><a name="bkmk_vc-string-editor-context-specific-shortcuts"></a> VC dize Düzenleyicisi: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komut|Klavye kısayolu|Komut KIMLIĞI|
|-|-|-|
|Yeni dize|**Ekle**| Edit.NewString |

### <a name="view-designer-context-specific-shortcuts"></a><a name="bkmk_view-designer-context-specific-shortcuts"></a> Görünüm Tasarımcısı: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Veri almayı iptal et|**CTRL + T**| QueryDesigner.CancelRetrievingData |
|Ölçütler|**Ctrl+2**| QueryDesigner.Criteria |
|Diyagram|**CTRL + 1**| QueryDesigner.Diagram |
|SQL Yürüt|**Ctrl+R**| QueryDesigner.ExecuteSQL |
|Satıra git|**Ctrl+G**| QueryDesigner.GotoRow |
|JOIN modu|**Ctrl+Shift+J**| QueryDesigner.JoinMode |
|Sonuçlar|**Ctrl+4**| QueryDesigner.Results |
|Sql|**Ctrl+3**| QueryDesigner.SQL |

### <a name="visual-studio-context-specific-shortcuts"></a><a name="bkmk_visual-studio-context-specific-shortcuts"></a>Visual Studio: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komut|Klavye kısayolu|Komut KIMLIĞI|
|-|-|-|
|Yöntemler bölmesini gizle|**CTRL + 1**| OtherContextMenus.ORDesignerContext.HideMethodsPane |

### <a name="windows-forms-designer-context-specific-shortcuts"></a><a name="bkmk_windows-forms-designer-context-specific-shortcuts"></a>Windows Form Tasarımcısı: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Çizgiyi Böl|**Enter**| Edit.BreakLine |
|Sol karakter|**Sol Ok**| Edit.CharLeft |
|Karakter sola Genişlet|**Shift+Sol Ok**| Edit.CharLeftExtend |
|Sağ karakter|**Sağ Ok**| Edit.CharRight |
|Sağ karakter Genişlet|**Shift+Sağ Ok**| Edit.CharRightExtend |
|Belge sonu|**End**| Edit.DocumentEnd |
|Belge bitişi uzat|**Shift+End**| Edit.DocumentEndExtend |
|Belge başlangıcı|**Giriş Ekranı**| Edit.DocumentStart |
|Belge başlangıcını uzat|**Shift+Home**| Edit.DocumentStartExtend |
|Ekle sekmesi|**Sekme**| Edit.InsertTab |
|Aşağı satır|**Aşağı Ok**| Edit.LineDown |
|Çizgi aşağı genişletme|**Shift+Yukarı Ok**| Edit.LineDownExtend |
|Sırala|**Yukarı Ok**| Edit.LineUp |
|Genişletmeyi yukarı doğru sırala|**Shift+Aşağı Ok**| Edit.LineUpExtend |
|Denetimi aşağı taşıma|**Ctrl+Aşağı Ok**| Edit.MoveControlDown |
|Denetimi sola taşıma|**Ctrl+Sol Ok**| Edit.MoveControlLeft |
|Denetimi sağa taşıma|**Ctrl+Sağ Ok**| Edit.MoveControlRight |
|Denetimi yukarı taşıma|**Ctrl+Yukarı Ok**| Edit.MoveControlUp |
|Seçim iptali|**Esc**| Edit.SelectionCancel |
|Boyut denetimi aşağı|**Ctrl+Shift+Aşağı Ok**| Edit.SizeControlDown |
|Boyut denetimi sola|**Ctrl+Shift+Sol Ok**| Edit.SizeControlLeft |
|Boyut denetimi hakkı|**Ctrl+Shift+Sağ Ok**| Edit.SizeControlRight |
|Boyut denetimi|**Ctrl+Shift+Yukarı Ok**| Edit.SizeControlUp |
|Sekme sol|**Shift+Sekme Tuşu**| Edit.TabLeft |

### <a name="work-item-editor-context-specific-shortcuts"></a><a name="bkmk_work-item-editor-context-specific-shortcuts"></a> İş Öğesi Düzenleyicisi: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|İş öğesinin kopyasını oluşturma|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|İş öğesini yenileme|**F5**| Edit.RefreshWorkItem |
|Yeni bağlantılı iş öğesi|**Shift+Alt+L**| Team.NewLinkedWorkItem |

### <a name="work-item-query-view-context-specific-shortcuts"></a><a name="bkmk_work-item-query-view-context-specific-shortcuts"></a> İş Öğesi Sorgu Görünümü: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|İş öğesinin kopyasını oluşturma|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|Girinti|**Shift+Alt+Sağ Ok**| Edit.Indent |
|Outdent|**Shift+Alt+Sol Ok**| Edit.Outdent |
|Yeni bağlantılı iş öğesi|**Shift+Alt+L**| Team.NewLinkedWorkItem |
|Yenile|**F5**| Team.Refresh |
|İki Durumlu Düğme|**Shift+Alt+V**| Window.Toggle |

### <a name="work-item-results-view-context-specific-shortcuts"></a><a name="bkmk_work-item-results-view-context-specific-shortcuts"></a> İş Öğesi Sonuçları Görünümü: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|İş öğesinin kopyasını oluşturma|**Shift+Alt+C**| Edit.CreateCopyofWorkItem |
|Girinti|**Shift+Alt+Sağ Ok**| Edit.Indent |
|Outdent|**Shift+Alt+Sol Ok**| Edit.Outdent |
|Sonraki iş öğesine var|**Shift+Alt+N**| Team.GotoNextWorkItem |
|Önceki iş öğesine giriş|**Shift+Alt+P**| Team.GotoPreviousWorkItem |
|Yeni bağlantılı iş öğesi|**Shift+Alt+L**| Team.NewLinkedWorkItem |
|Yenile|**F5**| Team.Refresh |
|İki Durumlu Düğme|**Shift+Alt+V**| Window.Toggle |

### <a name="workflow-designer-context-specific-shortcuts"></a><a name="bkmk_workflow-designer-context-specific-shortcuts"></a> İş Akışı Tasarımcısı: içeriğe özgü kısayollar

Bu içeriğe özgü kısayollar şunlardır:


|Komutlar|Klavye kısayolları|Komut KIMLIĞI|
|-|-|-|
|Sözcüğü Tamam|**Ctrl+K, W**<br /><br /> veya<br /><br /> **Ctrl+K, Ctrl+W**<br /><br /> veya<br /><br /> **Ctrl+Ara Çubuğu**<br /><br /> veya<br /><br /> **Alt+Sağ Ok**| Edit.CompleteWord |
|Filtre düzeyini azalt|**Alt+,**| Edit.DecreaseFilterLevel |
|Filtre düzeyini artır|**Alt +.**| Edit.IncreaseFilterLevel |
|Üyeleri Listele|**Ctrl+K, L**<br /><br /> veya<br /><br /> **Ctrl+K, Ctrl+L**<br /><br /> veya<br /><br /> **Ctrl+J**| Edit.ListMembers |
|Parametre bilgisi|**Ctrl+K, P**<br /><br /> veya<br /><br /> **Ctrl+K, Ctrl+P**<br /><br /> veya<br /><br /> **Ctrl+Shift+Ara Çubuğu**| Edit.ParameterInfo |
|Hızlı bilgi|**Ctrl+K, I**<br /><br /> veya<br /><br /> **Ctrl+K, Ctrl+I**| Edit.QuickInfo |
|Daralt|**Ctrl+E, Ctrl+C**<br /><br /> veya<br /><br /> **Ctrl+E, C**| WorkflowDesigner.Collapse |
|Tümünü daralt|veya| WorkflowDesigner.CollapseAll |
|Bağlan düğümleri|**Ctrl+E, Ctrl+F**<br /><br /> veya<br /><br /> **Ctrl+E, F**| WorkflowDesigner.ConnectNodes |
|Değişken Oluştur|**Ctrl+E, Ctrl+N**<br /><br /> veya<br /><br /> **Ctrl+E, N**| WorkflowDesigner.CreateVariable |
|Tümünü genişlet|**Ctrl+E, Ctrl+X**<br /><br /> veya<br /><br /> **Ctrl+E, X**| WorkflowDesigner.ExpandAll |
|Yerinde Genişlet|**Ctrl+E, Ctrl+E**<br /><br /> veya<br /><br /> **Ctrl+E, E**| WorkflowDesigner.ExpandInPlace |
|Üst öğeye git|**Ctrl+E, Ctrl+P**<br /><br /> veya<br /><br /> **Ctrl+E, P**| WorkflowDesigner.GoToParent |
|Odağı taşı|**Ctrl+E, Ctrl+M**<br /><br /> veya<br /><br /> **Ctrl+E, M**| WorkflowDesigner.MoveFocus |
|Tasarımcı üzerinden gezinme|**Ctrl+Alt+F6**| WorkflowDesigner.NavigateThroughDesigner |
|Geri Yükleme|**Ctrl+E, Ctrl+R**<br /><br /> veya<br /><br /> **Ctrl+E, R**| WorkflowDesigner.Restore |
|Bağımsız değişken tasarımcısını gizleme göster|**Ctrl+E, Ctrl+A**<br /><br /> veya<br /><br /> **Ctrl+E, A**| WorkflowDesigner.ShowHideArgumentDesigner |
|İçeri aktarmaları tasarımcısını göster|**Ctrl+E, Ctrl+I**<br /><br /> veya<br /><br /> **Ctrl+E, I**| WorkflowDesigner.ShowHideImportsDesigner |
|Gizlemeye genel bakış haritasını gösterme|**Ctrl+E, Ctrl+O** ('O' harfi)<br /><br /> veya<br /><br /> **Ctrl+E, O**| WorkflowDesigner.ShowHideOverviewMap |
|Değişken tasarımcısını gizlemeyi göster|**Ctrl+E, Ctrl+V**<br /><br /> veya<br /><br /> **Ctrl+E, V**| WorkflowDesigner.ShowHideVariableDesigner |
|Seçimi iki durumlu olarak değiştir|**Ctrl+E, Ctrl+S**<br /><br /> veya<br /><br /> **Ctrl+E, S**| WorkflowDesigner.ToggleSelection |
|Yakınlaştır|**Ctrl+Num +**| WorkflowDesigner.ZoomIn |
|Uzaklaştır|**Ctrl+Num -**| WorkflowDesigner.ZoomOut |

### <a name="xaml-ui-designer-context-specific-shortcuts"></a><a name="bkmk_xaml-ui-designer-context-specific-shortcuts"></a> XAML KULLANıCı Arabirimi Tasarımcısı: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Hepsini sığdır|**Ctrl+0** (sıfır)| Design.FitAll |
|Tanıtıcıları göster|**F9**| Design.ShowHandles |
|Yakınlaştır|**Ctrl+Alt+=**| Design.ZoomIn |
|Uzaklaştır|**Ctrl+Alt+-**| Design.ZoomOut |
|Tasarımcı seçenekleri|**Ctrl+Shift+;**|
|Metin düzenleme|**F2**| Format.EditText |
|Tümü|**Ctrl+Shift+R**| Format.ResetLayout.All |
|Proje kodunu çalıştırma|**Ctrl+F9**|
|Gizle (yalnızca Blend)|**Ctrl+H**| Timeline.Hide (yalnızca Blend) |
|Kilit (yalnızca Blend)|**Ctrl+L**| Timeline.Lock (yalnızca Blend) |
|Göster (yalnızca Blend)|**Ctrl+Shift+H**| Timeline.Show (yalnızca Blend) |
|Kilit açma (yalnızca Blend)|**Ctrl+Shift+L**| Timeline.Unlock (yalnızca Blend) |
|Kenar sol hareket sola|**Ctrl+Shift+,**| View.EdgeLeftMoveLeft |
|Kenar sol hareket sağ|**Ctrl+Shift+.**| View.EdgeLeftMoveRight |
|Kenar sağ hareket sola|**Ctrl+Shift+Alt+,**| View.EdgeRightMoveLeft |
|Kenar sağ taşı|**Ctrl+Shift+Alt+.**| View.EdgeRightMoveRight |
|Özellik işaretçisini göster menüsü|**Ctrl+Ara Çubuğu**| View.ShowPropertyMarkerMenu |

### <a name="xml-text-editor-context-specific-shortcuts"></a><a name="bkmk_xml-text-editor-context-specific-shortcuts"></a> XML (Metin) Düzenleyicisi: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|XSLT hata ayıklamayı başlatma|**Alt+F5**| XML.StartXSLTDebugging |
|Hata ayıklama olmadan XSLT'i başlatma|**Ctrl+Alt+F5**| XML.StartXSLTWithoutDebugging |

### <a name="xml-schema-designer-context-specific-shortcuts"></a><a name="bkmk_xml-schema-designer-context-specific-shortcuts"></a> XML Şema Tasarımcısı: bağlama özgü kısayollar

Bu bağlama özgü kısayollar:


|Komutlar|Klavye kısayolları|Komut Kimliği|
|-|-|-|
|Aşağıdan yukarıya|**Alt+Yukarı Ok**| GraphView.BottomtoTop |
|Soldan sağa|**Alt+Sağ Ok**| GraphView.LefttoRight |
|Sağdan sola|**Alt+Sol Ok**| GraphView.RighttoLeft |
|Üstten aşağıya|**Alt+Aşağı Ok**| GraphView.ToptoBottom |
|Çalışma alanından kaldırma|**Silme**| OtherContextMenus.GraphView.RemovefromWorkspace |
|İçerik modeli görünümünü gösterme|**Ctrl+2**| XsdDesigner.ShowContentModelView |
|Grafik görünümünü göster|**Ctrl+3**| XsdDesigner.ShowGraphView |
|Başlangıç görünümünü göster|**Ctrl+1**| XsdDesigner.ShowStartView |

