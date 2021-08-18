---
title: Komut Diğer Adları
description: Komut yürütmek istediğiniz zaman daha az karakter yazarak komut diğer adlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e735a2a4d519cb785ca37f3cf57a55f2d901c4ee
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122116857"
---
# <a name="visual-studio-command-aliases"></a>Visual Studio Komut Diğer Adları

Komut diğer adları, bir komutu yürütmek istediğiniz zaman daha az karakter yazmana izin sağlar. Diğer adları **Bul/Komut kutusuna veya Komut** penceresine **girersiniz.** Örneğin, Dosya Aç iletişim kutusunu görüntülemek için girmek `>File.OpenFile` yerine önceden tanımlanmış diğer adını kullanabilirsiniz.  `>of`

Geçerli `alias` diğer **adların** ve tanımlarının listesini görüntülemek için Komut penceresine yazın. Komut `>cls` penceresinin içeriğini temizlemek için **yazın.** Belirli bir komutun diğer adını görmek için `alias <command name>` yazın.

Bağımsız değişken komutlarından biri (bağımsız değişkenlerle veya bağımsız değişkenler olmadan) Visual Studio kolayca kendi diğer adlarınızı oluşturabilirsiniz. Örneğin, diğer ad için söz dizimi `File.NewFile MyFile.txt` şu `alias MyAlias File.NewFile MyFile.txt` şekildedir: . Diğer adlardan birini şu adlarla silebilirsiniz: `alias <alias name> /delete`

Aşağıdaki tabloda, önceden tanımlanmış komut diğer adlarının Visual Studio yer alır. Bazı komut adlarının birden fazla önceden tanımlanmış diğer adı vardır. Doğru söz dizimlerini, bağımsız değişkenleri ve bu komutların anahtarlarını açıklayan ayrıntılı konuları görüntülemek için aşağıdaki komut adlarının bağlantılarına tıklayın.

|Komut Adı|Diğer ad|Tam Ad|
|------------------|-----------|-------------------|
|[Yazdır Komutu](../../ide/reference/print-command.md)|?|Print|
|[Hızlı İzleme Komutu](../../ide/reference/quick-watch-command.md)|??|Debug.Quickwatch|
|Yeni Project|AddProj|File.AddNewProject|
|[Diğer Ad Komutu](../../ide/reference/alias-command.md)|Diğer ad|Tools.Alias|
|Otomatik değişkenler penceresi|Otomobil|Debug.Autos|
|Kesme Noktaları penceresi|Bl|Debug.Breakpoints|
|Kesme Noktası'nın Geçişini Değiştir|Bp|Debug.ToggleBreakPoint|
|Çağrı Yığını penceresi|CallStack|Debug.CallStack|
|Yer İşaretlerini Temizleme|ClearBook|Edit.ClearBookmarks|
|Kapat|Kapat|File.Close|
|Tüm Belgeleri Kapat|Closeall|Window.CloseAllDocuments|
|Tümünü Temizle|Cls|Edit.ClearAll|
|Komut modu|cmd|View.CommandWindow|
|Kodu Görüntüle|kod|View.ViewCode|
|[Belleği Listele Komutu](../../ide/reference/list-memory-command.md)|d|Debug.ListMemory|
|[Bellek Komutunu](../../ide/reference/list-memory-command.md) ANSI Olarak Listele|Savcı|Debug.ListMemory /Ansi|
|[List Memory Command](../../ide/reference/list-memory-command.md) One-Byte biçimi|Db|Debug.ListMemory /Format:OneByte|
|[Bellek Komutunu, bellek](../../ide/reference/list-memory-command.md) biçimiyle ANSI Four-Byte listele|Dc|Debug.ListMemory /Format:FourBytes /Ansi|
|[List Memory Command](../../ide/reference/list-memory-command.md) Four-Byte biçimi|Ekle|Debug.ListMemory /Format:FourBytes|
|BOL'ye sil|DelBOL|Edit.DeleteToBOL|
|EOL'ye sil|DelEOL|Edit.DeleteToEOL|
|Yatay Boşluğu Silme|DelHSp|Edit.DeleteHorizontalWhitespace|
|Görünüm Tasarımcısı|tasarımcı|View.ViewDesigner|
|[Belleği Listele Komutu](../../ide/reference/list-memory-command.md) Kayan biçim|Df|Debug.ListMemory/Format:Float|
|Ayrıştırma penceresi|disasm|Debug.Disassembly|
|[List Memory Command](../../ide/reference/list-memory-command.md) Eight-Byte biçimi|Dq|Debug.ListMemory /Format:EightBytes|
|[Belleği Unicode Olarak](../../ide/reference/list-memory-command.md) Listele Komutu|Du|Debug.ListMemory /Unicode|
|[Deyimi Değerlendir Komutu](../../ide/reference/evaluate-statement-command.md)|değerlendirme|Debug.EvaluateStatement|
|Çıkış|Çıkış|File.Exit|
|Biçim Seçimi|biçim|Edit.FormatSelection|
|Tam Ekran|Fullscreen|View.FullScreen|
|[Başlat Komutu](../../ide/reference/start-command.md)|g|Debug.Start|
|[Komuta Git](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|
|Ayraç'a gidin|GotoBrace|Edit.GotoBrace|
|F1Help|Help|Help.F1Help|
|Anlık Mod|immed|Tools.ImmediateMode|
|Dosyayı Metin Olarak Ekle|InsertFile|Edit.InsertFileAsText|
|[Çağrı Yığınını Listele Komutu](../../ide/reference/list-call-stack-command.md)|Kb|Debug.ListCallStack|
|Küçük Harf Yapma|Lcase|Edit.MakeLowercase|
|Satırı Kes|LineCut|Edit.LineCut|
|Satır Sil|LineDel|Edit.LineDelete|
|Üyeleri Listeleme|ListMembers|Edit.ListMembers|
|Yerel öğeler penceresi|Yerli|Debug.Locals|
|[Günlük Komutu Penceresi Çıkış Komutu](../../ide/reference/log-command-window-output-command.md)|Günlük|Tools.LogCommandWindowOutput|
|Komut Penceresi İşaret modu|mark|Tools.CommandWindowMarkMode|
|Bellek penceresi|Bellek Belleği1|Debug.Memory1|
|Bellek Penceresi 2|Bellek2|Debug.Memory2|
|Bellek Penceresi 3|Bellek3|Debug.Memory3|
|Bellek Penceresi 4|Bellek4|Debug.Memory4|
|[Radix Komutunu Ayarlama](../../ide/reference/set-radix-command.md)|n|Debug.SetRadix|
|[ShowWebBrowser Komutu](../../ide/reference/showwebbrowser-command.md)|gezinti gezintisi|View.ShowWebBrowser|
|Sonraki Yer İşareti|Nextbook|Edit.NextBookmark|
|[Yeni Dosya Komutu](../../ide/reference/new-file-command.md)|Nf|File.NewFile|
|Yeni Proje|np NewProj|File.NewProject|
|[Dosya Aç Komutu](../../ide/reference/open-file-command.md)|açık|File.OpenFile|
|[Komut Project Aç](../../ide/reference/open-project-command.md)|Op|File.OpenProject|
|Tanımları Daralt/AçıklamaYı Durdur|OutlineDefs StopOutlining|Edit.CollapseToDefinitions|
|Adım At|p|Debug.StepOver|
|Parametre Bilgileri|ParamInfo|Edit.ParameterInfo|
|Dışarı Adımla|pr|Debug.StepOut|
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

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
