---
title: Komut Takma Adları
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596417"
---
# <a name="visual-studio-command-aliases"></a>Visual Studio Komut Diğer Adları

Komut takma adları, bir komutu yürütmek istediğinizde daha az karakter yazmanıza izin vermez. Diğer adları **Bul/Komut** kutusuna veya **Komut** penceresine girersiniz. Örneğin, **Dosya aç** `>File.OpenFile` iletişim kutusunu görüntülemek için girmek yerine, önceden tanımlanmış diğer `>of`adı kullanabilirsiniz.

Geçerli `alias` diğer adların ve tanımlarının listesini görüntülemek için **Komut** penceresini yazın. Komut `>cls` penceresinin içeriğini **Command** temizlemek için yazın. Belirli bir komutiçin takma ad görmek istiyorsanız, `alias <command name>`yazın.

Visual Studio komutlarından biri için (bağımsız veya bağımsız) kendi takma adınızı kolayca oluşturabilirsiniz. Örneğin, diğer adı takma sözcük için `File.NewFile MyFile.txt` sözdizimi. `alias MyAlias File.NewFile MyFile.txt` Diğer adlarınızdan birini`alias <alias name> /delete`

Aşağıdaki tabloda önceden tanımlanmış Visual Studio komut diğer adlarının bir listesi yer almaktadır. Bazı komut adlarının birden fazla önceden tanımlanmış takma adı vardır. Bu komutlar için doğru sözdizimini, bağımsız değişkenleri ve anahtarları açıklayan ayrıntılı konuları görüntülemek için aşağıdaki komut adları için bağlantıları tıklatın.

|Komut Adı|Diğer ad|Tam Adı|
|------------------|-----------|-------------------|
|[Yazdır Komutu](../../ide/reference/print-command.md)|?|Print|
|[Hızlı Bakış Komutu](../../ide/reference/quick-watch-command.md)|??|Debug.Quickwatch|
|Yeni Proje Ekle|AddProj|File.AddNewProject|
|[Diğer Ad Komutu](../../ide/reference/alias-command.md)|Diğer ad|Araçlar.Alias|
|Otomatik değişkenler penceresi|Otomobil|Debug.Autos|
|Kesme Noktaları penceresi|Bl|Debug.Breakpoints|
|Kesme Noktasını Geçiş|Bp|Hata Ayıklama.ToggleBreakPoint|
|Çağrı Yığını penceresi|CallStack|Debug.CallStack|
|Yer Imlerini Temizle|ClearBook|Edit.ClearBookmarks|
|Kapat|Kapat|Dosya.Kapat|
|Tüm Belgeleri Kapat|Closeall|Pencere.CloseTüm Belgeler|
|Tümünü Temizle|Cls|Edit.ClearAll|
|Komut modu|cmd|View.CommandWindow|
|Kodu Görüntüle|kod|View.ViewCode|
|[Liste Bellek Komutu](../../ide/reference/list-memory-command.md)|d|Debug.ListMemory|
|[Bellek Komutunu](../../ide/reference/list-memory-command.md) ANSI olarak listele|Savcı|Debug.ListBellek /Ansi|
|[Liste Bellek Komutu](../../ide/reference/list-memory-command.md) Tek Bayt biçimi|Db|Debug.ListBellek /Biçim:OneByte|
|[Bellek Komutunu](../../ide/reference/list-memory-command.md) Dört Bayt formatında ANSI olarak listele|Dc|Debug.ListMemory /Format:FourBytes /Ansi|
|[Liste Bellek Komutu](../../ide/reference/list-memory-command.md) Dört Bayt biçimi|Ekle|Debug.ListBellek /Biçim:FourBytes|
|BOL'a sil|DelBOL|Düzenle.DeleteToBOL|
|EOL'ye silme|DelEOL|Düzenle.DeleteToEOL|
|Yatay Boşluk Silme|DelHSp|Düzenle.DeleteHorizontalWhitespace|
|Görünüm Tasarımcısı|tasarımcı|View.ViewDesigner|
|[Liste Bellek Komutu](../../ide/reference/list-memory-command.md) Float biçimi|Df|Debug.ListMemory/Format:Float|
|Ayrıştırma penceresi|disasm|Debug.Disassembly|
|[Liste Bellek Komutu](../../ide/reference/list-memory-command.md) Sekiz Bayt biçimi|Dq|Debug.ListBellek /Biçim:EightBytes|
|[Bellek Komutunu](../../ide/reference/list-memory-command.md) Unicode olarak listele|Du|Hata Ayıklama.ListBellek /Unicode|
|[Deyimi Değerlendir Komutu](../../ide/reference/evaluate-statement-command.md)|eval|Debug.EvaluateStatement|
|Çık|Çık|File.Exit|
|Biçim Seçimi|biçim|Edit.FormatSelection|
|Tam Ekran|Fullscreen|View.FullScreen|
|[Başlat Komutu](../../ide/reference/start-command.md)|g|Debug.Start|
|[Git Komutu](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|
|Ayraç'a git|GotoBrace|Edit.GotoBrace|
|F1Help|Yardım|Help.F1Help|
|Hemen Mod|immed|Araçlar.ImmediateMode|
|Dosyayı Metin Olarak Ekleme|Dosya Yı Ekle|Edit.InsertFileAsText|
|[Liste Çağrı Yığını Komutu](../../ide/reference/list-call-stack-command.md)|Kb|Debug.ListCallStack|
|Küçük Harf Yapma|Lcase|Edit.MakeLowercase|
|Kesme Hattı|LineCut|Edit.LineCut|
|Satır Sil|LineDel|Edit.LineDelete|
|Üyeleri Listeleme|Liste Üyeleri|Edit.ListMembers|
|Yerel öğeler penceresi|Yerli|Debug.Locals|
|[Günlük Komut Penceresi Çıkış Komutu](../../ide/reference/log-command-window-output-command.md)|Günlük|Tools.LogCommandWindowOutput|
|Komut Penceresi İşaret modu|işareti|Tools.CommandWindowMarkMode|
|Bellek penceresi|Bellek Bellek1|Debug.Memory1|
|Bellek Penceresi 2|Bellek2|Debug.Memory2|
|Bellek Penceresi 3|Bellek3|Debug.Memory3|
|Bellek Penceresi 4|Bellek4|Debug.Memory4|
|[Sayı Tabanını Ayarla Komutu](../../ide/reference/set-radix-command.md)|n|Debug.SetRadix|
|[ShowWebBrowser Komutu](../../ide/reference/showwebbrowser-command.md)|gezinmek|View.ShowWebBrowser|
|Sonraki Yer İşareti|Nextbook|Edit.NextBookmark|
|[Yeni Dosya Komutu](../../ide/reference/new-file-command.md)|Nf|File.NewFile|
|Yeni Proje|np NewProj|File.NewProject|
|[Dosya Aç Komutu](../../ide/reference/open-file-command.md)|onun Açık|File.OpenFile|
|[Açık Proje Komutu](../../ide/reference/open-project-command.md)|Op|File.OpenProject|
|Tanımlara Daralt/Anahat Oluşturmayı Durdur|AnahatDefs StopOutlining|Edit.CollapseToDefinitions|
|Adım Adım|p|Debug.StepOver|
|Parametre Bilgileri|ParamInfo|Edit.ParameterInfo|
|Dışarı Adım|Pr|Debug.StepOut|
|Önceki Yer İşareti|PrevBook|Edit.PreviousBookmark|
|Dosya Yazdırma|yazdır|File.Print|
|Özellikler Penceresi|Sahne|View.PropertiesWindow|
|Durdur|q|Debug.StopDebugging|
|Yinele|Yinele|Edit.Redo|
|Yazmaçlar penceresi|yazmaçlar|Debug.Registers|
|İmlec'e Çalıştır|Rtc|Debug.RunToCursor|
|Seçili Öğeleri Kaydet|save|File.SaveSelectedItems|
|Tümünü Kaydet|SaveAll|File.SaveAll|
|Farklı Kaydet|Saveas|Dosya.SaveSelectedItemsAs|
|[Kabuk Komutu](../../ide/reference/shell-command.md)|kabuk|Araçlar.Kabuk|
|Dosyalarda Bul'u Durdur|StopFind|Edit.FindInFiles /stop|
|Takas Çapası|SwapAnchor|Edit.SwapAnchor|
|Adım Adım|t|Debug.StepInto|
|Tabify Seçimi|sekmelere ayırma|Edit.TabifySelection|
|Görev Listesi penceresi|Tasklist|View.TaskList|
|İş Parçacıkları penceresi|İş Parçacıkları|Debug.Threads|
|Yatay Döşeme|ÇiniH|Pencere.TileYatay olarak|
|Dikey Döşeme|ÇinilV|Pencere.FayansDikey|
|Yer İşaretini Değiştir|ToggleBook|Edit.ToggleBookmark|
|Araç kutusu penceresi|araç kutusu|View.Toolbox|
|[Ayrıştırılmış Kodu Listele Komutu](../../ide/reference/list-disassembly-command.md)|u|Debug.ListDisassembly|
|Büyük Harf Yap|Ucase|Edit.MakeUppercase|
|Geri al|Geri alma|Edit.Undo|
|Untabify Seçimi|Untabify|Edit.UntabifySelection|
|Gözcü penceresi|İzle|Hata Ayıklama.WatchN|
|Sözcük Kaydırma'yı Geçiş|WordWrap|Edit.ToggleWordWrap|
|Liste İşlemleri|&#124;|Hata Ayıklama.ListProcesses|
|[Liste Konuları Komutu](../../ide/reference/list-threads-command.md)|~ ~*k\*~ kb|Debug.ListThreads Debug.ListTheads / AllThreads|

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
