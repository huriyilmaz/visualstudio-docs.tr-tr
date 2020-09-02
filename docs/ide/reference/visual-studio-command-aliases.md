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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b420644672309371ab61f1499e22d4745c69c569
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596417"
---
# <a name="visual-studio-command-aliases"></a>Visual Studio Komut Diğer Adları

Komut diğer adları, bir komutu yürütmek istediğinizde daha az karakter yazmanız sağlar. **Bul/komut** kutusu veya **komut** penceresine diğer adlar girersiniz. Örneğin, `>File.OpenFile` **Dosya Aç** iletişim kutusunu göstermek için girmek yerine önceden tanımlanmış diğer adı kullanabilirsiniz `>of` .

`alias`Geçerli diğer adların ve tanımlarının bir listesini göstermek Için **komut** penceresine yazın. `>cls` **Komut** penceresinin içeriğini temizlemek için yazın. Belirli bir komut için bir diğer ad görmek isterseniz, yazın `alias <command name>` .

Visual Studio komutlarından biri (bağımsız değişkenlerle veya olmayan) için kendi diğer adınızı kolayca oluşturabilirsiniz. Örneğin, diğer ad için sözdizimi `File.NewFile MyFile.txt` `alias MyAlias File.NewFile MyFile.txt` . Diğer adlarınızın birini ile silebilirsiniz `alias <alias name> /delete`

Aşağıdaki tablo, önceden tanımlanmış Visual Studio komut diğer adlarının listesini içerir. Bazı komut adlarında birden fazla önceden tanımlanmış diğer ad var. Bu komutların doğru söz dizimini, bağımsız değişkenlerini ve anahtarlarını açıklayan ayrıntılı konuları göstermek için aşağıdaki komut adlarına yönelik bağlantılara tıklayın.

|Komut adı|Diğer ad|Ad Tamam|
|------------------|-----------|-------------------|
|[Yazdır komutu](../../ide/reference/print-command.md)|?|Hata Ayıkla. Yazdır|
|[Hızlı Izle komutu](../../ide/reference/quick-watch-command.md)|??|Hata Ayıkla. QuickWatch|
|Yeni Proje Ekle|AddProj|File. AddNewProject|
|[Alias komutu](../../ide/reference/alias-command.md)|Diğer ad|Tools. Alias|
|Otomatik değişkenler penceresi|Otolar|Debug.Autos|
|Kesme Noktaları penceresi|BL|Debug.Breakpoints|
|Kesme noktasını aç|BP|Debug. ToggleBreakPoint|
|Çağrı Yığını penceresi|Çağrı yığını|Debug.CallStack|
|Yer Imlerini temizle|ClearBook|Edit.ClearBookmarks|
|Kapat|Kapat|File. Close|
|Tüm belgeleri kapat|CloseAll|Window. CloseAllDocuments|
|Tümünü Temizle|CLS|Düzenle. ClearAll|
|Komut modu|cmd|View.CommandWindow|
|Kodu Görüntüle|kod|View.ViewCode|
|[Belleği Listele komutu](../../ide/reference/list-memory-command.md)|d|Debug. ListMemory|
|[Bellek komutunu](../../ide/reference/list-memory-command.md) ANSI olarak Listele|kapattığımda|Debug. ListMemory/ANSI|
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
|[Ifadeyi değerlendir komutu](../../ide/reference/evaluate-statement-command.md)|Eval|Debug. EvaluateStatement|
|Çıkış|Çıkış|File.Exit|
|Biçim Seçimi|biçim|Edit.FormatSelection|
|Tam Ekran|Tam|View.FullScreen|
|[Başlat komutu](../../ide/reference/start-command.md)|g|Debug.Start|
|[Komuta git](../../ide/reference/go-to-command.md)|Sayfayln|Edit.GoTo|
|Küme ayracı 'na git|Sayfayayracı|Edit.GotoBrace|
|F1Help|Yardım|Help.F1Help|
|Anlık mod|immed|Tools. ImmediateMode|
|Dosyayı metin olarak ekle|InsertFile|. Insertfileastext 'yi Düzenle|
|[Çağrı yığınını Listele komutu](../../ide/reference/list-call-stack-command.md)|makalesinin|Debug. ListCallStack|
|Küçük harf yap|LCase|Edit.MakeLowercase|
|Satırı kes|LineCut|Edit.LineCut|
|Satır Sil|LineDel|Edit.LineDelete|
|Üyeleri Listeleme|ListMembers|Edit.ListMembers|
|Yerel öğeler penceresi|Ayarlanmalıdır|Debug.Locals|
|[Komut penceresi Çıkış komutunu günlüğe kaydet](../../ide/reference/log-command-window-output-command.md)|Günlük|Tools. LogCommandWindowOutput|
|Komut penceresi Işaret modu|işaretleyebilir|Tools. CommandWindowMarkMode|
|Bellek penceresi|Bellek Memory1|Debug.Memory1|
|Bellek penceresi 2|Memory2|Debug.Memory2|
|Bellek penceresi 3|Memory3|Debug.Memory3|
|Bellek penceresi 4|Memory4|Debug.Memory4|
|[Radix komutunu ayarla](../../ide/reference/set-radix-command.md)|n|Debug. SetRadix|
|[ShowWebBrowser komutu](../../ide/reference/showwebbrowser-command.md)|Gezinti gezme|View. ShowWebBrowser|
|Sonraki Yer İşareti|NextBook|Edit.NextBookmark|
|[Yeni dosya komutu](../../ide/reference/new-file-command.md)|NF|File.NewFile|
|Yeni Proje|NP NewProj|File.NewProject|
|[Dosya Aç komutu](../../ide/reference/open-file-command.md)|Açık|File.OpenFile|
|[Proje Aç komutu](../../ide/reference/open-project-command.md)|üs|File.OpenProject|
|Tanımlara Daralt/ana hattı durdur|OutlineDefs Stopouthizalama|Düzenle. CollapseToDefinitions|
|Adımla|p|Debug.StepOver|
|Parametre bilgileri|Paraınfo|Edit.ParameterInfo|
|Dışarı adımla|çekme isteği|Debug.StepOut|
|Önceki Yer İşareti|PrevBook|Edit.PreviousBookmark|
|Dosya Yazdırma|yazdır|File.Print|
|Özellikler Penceresi|props|View.PropertiesWindow|
|Durdur|q|Debug.StopDebugging|
|Yinele|Yinele|Edit.Redo|
|Yazmaçlar penceresi|yazmaçlar|Debug.Registers|
|Imlece kadar Çalıştır|malarını|Debug.RunToCursor|
|Seçili öğeleri kaydet|save|File.SaveSelectedItems|
|Tümünü Kaydet|SaveAll|File.SaveAll|
|Farklı Kaydet|Faklı|File. SaveSelectedItemsAs|
|[Kabuk komutu](../../ide/reference/shell-command.md)|kabuk|Tools. Shell|
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
|[Ayrıştırılmış kodu Listele komutu](../../ide/reference/list-disassembly-command.md)|u|Debug. ListDisassembly|
|Büyük harf yap|UCase|Edit.MakeUppercase|
|Geri Al|komutunu|Edit.Undo|
|Seçimi Kaldır|Sekme olmaktan kaldır|. Untabifi seçimini Düzenle|
|Gözcü penceresi|İzle|Debug. WatchN|
|Sözcük kaydırmayı aç|WordWrap|Edit.ToggleWordWrap|
|Işlem listeleme|&#124;|Debug. ListProcesses|
|[Iş parçacıklarını Listele komutu](../../ide/reference/list-threads-command.md)|~ ~ * k ~ \* KB|Debug. ListThreads hata ayıklama. ListTheads/AllThreads|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
