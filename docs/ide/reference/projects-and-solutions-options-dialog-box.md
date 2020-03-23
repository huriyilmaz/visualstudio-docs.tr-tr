---
title: Projeler ve Çözümler, Seçenekler iletişim kutusu
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ed60e07c625665f92838cfbc671b03c605fda0d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567651"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>Seçenekler iletişim kutusu: Projeler \> ve Çözümler Genel

Visual Studio'nun projeler ve çözümlerle ilgili davranışını tanımlamak için bu sayfayı kullanın. Bu seçeneklere erişmek için **Araç** > **Seçenekleri'ni**seçin, Projeleri **ve Çözümleri**genişletin ve ardından **Genel'i**seçin.

Aşağıdaki seçenekler **Genel** sayfada mevcuttur.

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>Yapı hatalarla bitiyorsa her zaman Hata Listesini göster

Yalnızca bir proje oluşturamazsa, yapı tamamlama da **Hata Listesi** penceresini açar. Yapı işlemi sırasında oluşan hatalar görüntülenir. Bu seçenek temizlendiğinde, hatalar yine de oluşur, ancak yapı tamamlandığında pencere açılmaz. Bu seçenek varsayılan olarak etkindir.

## <a name="track-active-item-in-solution-explorer"></a>Solution Explorer'da etkin öğeyi izleme

Seçildiğinde, **Solution Explorer** otomatik olarak açılır ve etkin öğe seçilir. Bir projeveya çözümdeki farklı dosyalarla veya tasarımcıdaki farklı bileşenlerle çalışırken seçili öğe değişir. Bu seçenek temizlendiğinde, **Solution Explorer'daki** seçim otomatik olarak değişmez. Bu seçenek varsayılan olarak etkindir.

## <a name="show-advanced-build-configurations"></a>Gelişmiş yapı yapılandırmalarını göster

Seçildiğinde, Yapı yapılandırma seçenekleri **Project Property Pages** iletişim kutusunda ve **Çözüm Özelliği Sayfaları** iletişim kutusunda görünür. Temizlendiğinde, yapı yapılandırma seçenekleri Project **Property Pages** iletişim kutusunda ve Visual Basic ve C# projeleri için bir yapılandırma veya iki yapılandırma hata ayıklama ve sürüm içeren **Çözüm Özelliği Sayfaları** iletişim kutusunda görünmez. Bir projenin kullanıcı tanımlı bir yapılandırması varsa, yapı yapılandırma seçenekleri gösterilir.

Seçilmediğinde, **Yapı** menüsündeki **Çözüm Oluştur,** **Çözüm Yap**ve Temiz **Çözüm**gibi komutlar Release yapılandırmasında gerçekleştirilir ve **Hata Ayıklama** menüsündeki Hata Ayıklama ve Hata **Ayıklama Olmadan Başlat**gibi komutlar Hata **Ayıklama** yapılandırmasında gerçekleştirilir.

## <a name="always-show-solution"></a>Her zaman çözümü göster

Seçildiğinde, çözüm ve çözümlerüzerinde hareket eden tüm komutlar her zaman IDE'de gösterilir. Temizlendiğinde, tüm projeler tek başına projeler olarak oluşturulur ve çözüm yalnızca bir proje içeriyorsa Çözüm Gezgini'nde veya IDE'de çözümlerüzerinde hareket eden komutlarda çözüm görmezsiniz.

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>Oluşturulduğunda yeni projeleri kaydetme

Seçildiğinde, **Yeni Proje** iletişim kutusunda projeniz için bir konum belirtebilirsiniz. Temizlendiklerinde, tüm yeni projeler geçici proje olarak oluşturulur. Geçici projelerle çalışırken, bir disk konumu belirtmenize gerek kalmadan bir proje oluşturabilir ve deneme yapabilirsiniz.

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>Proje konumuna güvenolmadığında kullanıcıyı uyar

Yeni bir proje oluşturmaya veya varolan bir projeyi tam olarak güvenilmeyen bir konumda açmaya çalışırsanız (örneğin, unc yolunda veya HTTP yolunda), bir ileti görüntülenir. Tam olarak güvenilmeyen bir konumda proje oluşturmaya veya açmaya çalıştığınızher seferde iletinin görüntülenip görüntülenmediğini belirtmek için bu seçeneği kullanın.

## <a name="show-output-window-when-build-starts"></a>Oluşturma başladığında Çıktı pencereni göster

Çözüm oluşturur başında IDE'deki [Çıkış penceresini](../../ide/reference/output-window.md) otomatik olarak görüntüler.

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Dosyaları yeniden adlandırırken sembolik yeniden adlandırma istemi

Seçildiğinde Visual Studio, projedeki tüm başvuruları kod öğesine yeniden adlandırıp adlandırmaması gerektiğini soran bir ileti kutusu görüntüler.

## <a name="prompt-before-moving-files-to-a-new-location"></a>Dosyaları yeni bir konuma taşımadan önce komut istemi

Seçildiğinde, Visual Studio dosyaların konumları **Solution Explorer'daki**eylemlerle değiştirilmeden önce bir onay iletisi kutusu görüntüler.

## <a name="reopen-documents-on-solution-load"></a>Çözüm yüküyle ilgili belgeleri yeniden açma

Seçildiğinde, çözüm kapatıldığında açık bırakılan belgeler, çözüm açıldığında otomatik olarak açılır.

Belirli dosya türlerinin veya tasarımcıların yeniden açılması çözüm yükünü geciktirebilir. Çözümün önceki bağlamını geri yüklemek [istemiyorsanız, çözüm yük performansını artırmak](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) için bu seçeneğin işaretlerini kaldırın.

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>Çözüm yükünde Çözüm Gezgini proje hiyerarşisi durumunu geri yükleme

Seçildiğinde, çözüm en son açıldığında genişletilip genişletilmediklerine veya daraltılıp sürülmediklerine göre Çözüm Gezgini'ndeki düğümlerin durumunu geri yüklenir. Büyük çözümler için çözüm yükleme süresini azaltmak için bu seçeneği seçin.

> [!TIP]
> Bu seçeneği devre dışı kederseniz, Çözüm Gezgini'ndeki etkin belgeye gezinmenin kolay bir **yolu, Çözüm Gezgini** araç çubuğunda **Etkin Belgeyle Eşitle'yi** seçmektir.
>
> ![Solution Explorer'da etkin belgeyle eşitleme](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>Çift tıklatarak veya Enter tuşuna basarak SDK tarzı proje dosyalarını açma

Bu seçenek seçildiğinde ve Solution Explorer'da SDK tarzı bir proje düğümüne çift **Enter**tıkladığınızda veya onu \*seçince ve sonra Enter tuşuna bastığınızda, proje dosyası (örneğin, .csproj dosyası) düzenleyicide XML olarak açılır. Seçildiğinde, Çözüm Gezgini'nde SDK tarzı bir proje düğümüne çift tıklayarak veya seçerek **Enter** tuşuna basarak düğümü yalnızca genişletme veya daraltma etkisi vardır.

Bu seçeneği seçmediyseniz ve SDK tarzı bir proje dosyasını yeniden güncelleştirmek istiyorsanız, Çözüm Gezgini'ndeki proje düğümüne sağ tıklayın ve **Proje Dosyasını Edit'i**seçin. Diğer proje türleri için, visual studio'da düzenlemeden önce projeyi boşaltmanız gerekir.

> [!TIP]
> *Bir SDK tarzı proje*, veya proje [SDK](../../msbuild/how-to-use-project-sdk.md), MSBuild 15.0 ile tanıtıldı daha yeni, daha aerodinamik proje dosyası biçimi vardır. SDK tarzı bir proje, örneğin `Sdk` `Project` `<Project Sdk="Microsoft.NET.Sdk">`öğe üzerinde bir öznitelik içerir. Visual Studio, örneğin Visual Studio şablonlarından birinden yeni bir .NET Core projesi oluşturduğunuzda SDK tarzı bir proje oluşturur.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler iletişim kutusu: Projeler \> ve Çözüm Konumları](projects-solutions-locations-options.md)
- [Seçenekler İletişim Kutusu, Projeler ve Çözümler, Derleme ve Çalıştırma](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Seçenekler İletişim Kutusu, Projeler ve Çözümler, Web Projeleri](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
