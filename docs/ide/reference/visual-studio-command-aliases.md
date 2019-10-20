---
title: Komut diğer adları
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- aliases, Visual Studio commands
- Visual Studio, commands
- predefined command aliases
- commands, aliases
- Visual Studio commands
- pre-defined command aliases
- command aliases
ms.assetid: de8bb378-8c1c-4087-a9a5-537fa8314c19
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac67e89ebf04979f8aec55f100e2b1138e9feb22
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72622255"
---
# <a name="visual-studio-command-aliases"></a>Visual Studio Komut Diğer Adları

Komut diğer adları, bir komutu yürütmek istediğinizde daha az karakter yazmanız sağlar. **Bul/komut** kutusu veya **komut** penceresine diğer adlar girersiniz. Örneğin, **Dosya Aç** iletişim kutusunu göstermek için `>File.OpenFile` girmek yerine, önceden tanımlanmış diğer ad `>of` kullanabilirsiniz.

Geçerli diğer adların ve tanımlarının bir listesini göstermek için **komut** penceresine `alias` yazın. **Komut** penceresinin içeriğini temizlemek için `>cls` yazın. Belirli bir komut için bir diğer ad görmek istiyorsanız `alias <command name>` yazın.

Visual Studio komutlarından biri (bağımsız değişkenlerle veya olmayan) için kendi diğer adınızı kolayca oluşturabilirsiniz. Örneğin, `File.NewFile MyFile.txt` diğer ad için sözdizimi `alias MyAlias File.NewFile MyFile.txt`. @No__t_0 diğer adlarınızın birini silebilirsiniz

Aşağıdaki tablo, önceden tanımlanmış Visual Studio komut diğer adlarının listesini içerir. Bazı komut adlarında birden fazla önceden tanımlanmış diğer ad var. Bu komutların doğru söz dizimini, bağımsız değişkenlerini ve anahtarlarını açıklayan ayrıntılı konuları göstermek için aşağıdaki komut adlarına yönelik bağlantılara tıklayın.

|Komut adı|Alias|Ad Tamam|
|------------------|-----------|-------------------|
|[Yazdır Komutu](../../ide/reference/print-command.md)|?|Hata Ayıkla. Yazdır|
|[Hızlı Bakış Komutu](../../ide/reference/quick-watch-command.md)|??|Hata Ayıkla. QuickWatch|
|Yeni Proje Ekle|AddProj|File. AddNewProject|
|[Diğer Ad Komutu](../../ide/reference/alias-command.md)|Alias|Tools. Alias|
|Otomatik değişkenler penceresi|Otolar|Debug.Autos|
|Kesme Noktaları penceresi|BL|Debug.Breakpoints|
|Kesme noktasını aç|BP|Debug. ToggleBreakPoint|
|Çağrı Yığını penceresi|Çağrı yığını|Debug.CallStack|
|Yer Imlerini temizle|ClearBook|Edit.ClearBookmarks|
|Close|Close|File. Close|
|Tüm belgeleri kapat|CloseAll|Window. CloseAllDocuments|
|Tümünü temizle|CLS|Düzenle. ClearAll|
|Komut modu|cmd|View.CommandWindow|
|Kodu görüntüle|kod|View.ViewCode|
|[Belleği Listele Komutu](../../ide/reference/list-memory-command.md)|d|Debug. ListMemory|
|[Bellek komutunu](../../ide/reference/list-memory-command.md) ANSI olarak Listele|Kapattığımda|Debug. ListMemory/ANSI|
|[Belleği Listele komutu](../../ide/reference/list-memory-command.md) Tek baytlık biçim|veritabanı|Debug. ListMemory/Format: OneByte|
|Dört baytlık biçimdeki [bellek komutunu](../../ide/reference/list-memory-command.md) ANSI olarak Listele|'ye|Debug. ListMemory/Format: on bayt/ANSI|
|[Belleği Listele komutu](../../ide/reference/list-memory-command.md) Dört baytlık biçim|Ekle|Debug. ListMemory/Format: on bayt|
|BOL 'a Sil|DelBOL|. DeleteToBOL 'yi Düzenle|
|EOL 'a Sil|DelEOL|Düzenle. DeleteToEOL|
|Yatay boşluğu Sil|DelHSp|. DeleteHorizontalWhitespace Düzenle|
|Görünüm Tasarımcısı|tasarımcı|View.ViewDesigner|
|[Belleği Listele komutu](../../ide/reference/list-memory-command.md) Kayan biçim|df|Debug. ListMemory/biçim: float|
|Ayrıştırma penceresi|DISASM|Debug.Disassembly|
|[Belleği Listele komutu](../../ide/reference/list-memory-command.md) Sekiz baytlık biçim|DQ|Debug. ListMemory/Format: sekizinci TBytes|
|[Bellek komutunu](../../ide/reference/list-memory-command.md) Unicode olarak Listele|du|Debug. ListMemory/UNICODE|
|[Deyimi Değerlendir Komutu](../../ide/reference/evaluate-statement-command.md)|Eval|Debug. EvaluateStatement|
|Çık|Çık|File.Exit|
|Biçim Seçimi|biçim|Edit.FormatSelection|
|Tam ekran|Tam|View.FullScreen|
|[Başlat Komutu](../../ide/reference/start-command.md)|Acil|Debug.Start|
|[Git Komutu](../../ide/reference/go-to-command.md)|Sayfayln|Edit.GoTo|
|Küme ayracı 'na git|Sayfayayracı|Edit.GotoBrace|
|F1Help|Yardım|Help.F1Help|
|Anlık mod|immed|Tools. ImmediateMode|
|Dosyayı metin olarak ekle|InsertFile|. Insertfileastext 'yi Düzenle|
|[Çağrı Yığınını Listele Komutu](../../ide/reference/list-call-stack-command.md)|makalesinin|Debug. ListCallStack|
|Küçük harf yap|LCase|Edit.MakeLowercase|
|Satırı kes|LineCut|Edit.LineCut|
|Satırı Sil|LineDel|Edit.LineDelete|
|Üyeleri Listeleme|ListMembers|Edit.ListMembers|
|Yerel öğeler penceresi|Ayarlanmalıdır|Debug.Locals|
|[Komut Penceresi Çıktısı Günlüğü Tut Komutu](../../ide/reference/log-command-window-output-command.md)|Günlük|Tools. LogCommandWindowOutput|
|Komut penceresi Işaret modu|işaretleyebilir|Tools. CommandWindowMarkMode|
|Bellek penceresi|Bellek Memory1|Debug.Memory1|
|Bellek penceresi 2|Memory2|Debug.Memory2|
|Bellek penceresi 3|Memory3|Debug.Memory3|
|Bellek penceresi 4|Memory4|Debug.Memory4|
|[Sayı Tabanını Ayarla Komutu](../../ide/reference/set-radix-command.md)|n|Debug. SetRadix|
|[ShowWebBrowser Komutu](../../ide/reference/showwebbrowser-command.md)|Gezinti gezme|View. ShowWebBrowser|
|Sonraki Yer İşareti|NextBook|Edit.NextBookmark|
|[Yeni Dosya Komutu](../../ide/reference/new-file-command.md)|NF|File.NewFile|
|Yeni proje|NP NewProj|File.NewProject|
|[Dosya Aç Komutu](../../ide/reference/open-file-command.md)|Açık|File.OpenFile|
|[Proje Aç Komutu](../../ide/reference/open-project-command.md)|üs|File.OpenProject|
|Tanımlara Daralt/ana hattı durdur|OutlineDefs Stopouthizalama|Düzenle. CollapseToDefinitions|
|Adımla|Lama|Debug.StepOver|
|Parametre bilgileri|Paraınfo|Edit.ParameterInfo|
|Dışarı adımla|çekme isteği|Debug.StepOut|
|Önceki Yer İşareti|PrevBook|Edit.PreviousBookmark|
|Dosya yazdır|yazdırdığımda|File.Print|
|Özellikler Penceresi|props|View.PropertiesWindow|
|Durdur|q|Debug.StopDebugging|
|Yinele|Yinele|Edit.Redo|
|Yazmaçlar penceresi|yazmaçlar|Debug.Registers|
|Imlece kadar Çalıştır|malarını|Debug.RunToCursor|
|Seçili öğeleri kaydet|Kaydet|File.SaveSelectedItems|
|Tümünü Kaydet|SaveAll|File.SaveAll|
|Farklı Kaydet|Faklı|File. SaveSelectedItemsAs|
|[Kabuk Komutu](../../ide/reference/shell-command.md)|kabuk|Tools. Shell|
|Dosyalarda bulmayı durdur|StopFind|Edit. Finınfiles/stop|
|Geçişi Değiştir|Swaptutturucu|Edit.SwapAnchor|
|Adımla|t|Debug.StepInto|
|Seçimi sekmeye Dönüştür|sekmelere ayırma|Edit. Tabifyıselection|
|Tasklist penceresi|KILL|View.TaskList|
|İş Parçacıkları penceresi|İş Parçacıkları|Debug.Threads|
|Yatay Döşe|TileH|Window. Tileyatay|
|Dikey Döşe|TileV|Window. Tiledikey|
|Yer İşaretini Değiştir|ToggleBook|Edit.ToggleBookmark|
|Araç kutusu penceresi|araç kutusu|View.Toolbox|
|[Ayrıştırılmış Kodu Listele Komutu](../../ide/reference/list-disassembly-command.md)|u|Debug. ListDisassembly|
|Büyük harf yap|UCase|Edit.MakeUppercase|
|Komutunu|komutunu|Edit.Undo|
|Seçimi Kaldır|Sekme olmaktan kaldır|. Untabifi seçimini Düzenle|
|Gözcü penceresi|Servisi|Debug. WatchN|
|Sözcük kaydırmayı aç|WordWrap|Edit.ToggleWordWrap|
|Işlem listeleme|&#124;|Debug. ListProcesses|
|[İş Parçacıklarını Listele Komutu](../../ide/reference/list-threads-command.md)|~ ~ * k ~ \*kb|Debug. ListThreads hata ayıklama. ListTheads/AllThreads|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)