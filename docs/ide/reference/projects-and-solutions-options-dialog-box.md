---
title: Projeler ve Çözümler, Seçenekler iletişim kutusu
description: Projeler ve Çözümler bölümündeki Genel sayfasını kullanarak proje ve çözümlerle ilgili Visual Studio davranışını tanımlamayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 14a37e634dea3ae40e78f02c82937a5d03c73e3f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151177"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>Seçenekler iletişim kutusu: Projeler ve Çözümler \> Genel

Projelerin proje ve Visual Studio davranışını tanımlamak için bu sayfayı kullanın. Bu seçeneklere erişmek için Araçlar **Seçenekleri'ne**  >  **tıklayın,** Projeler ve **Çözümler'i genişletin** ve ardından Genel'i **seçin.**

Genel sayfasında aşağıdaki seçenekler **kullanılabilir.**

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>Derleme hatalarla bitse her zaman Hata Listesini göster

Yalnızca **bir projenin derlemesi** başarısız olursa, derleme tamamlandığında Hata Listesi penceresini açar. Derleme işlemi sırasında oluşan hatalar görüntülenir. Bu seçenek temiz olduğunda hatalar yine de oluşur ancak derleme tamamlandığında pencere açılmaz. Bu seçenek varsayılan olarak etkindir.

## <a name="track-active-item-in-solution-explorer"></a>Etkin öğeyi Çözüm Gezgini

Seçildiğinde, **Çözüm Gezgini** olarak açılır ve etkin öğe seçilir. Bir proje veya çözümde farklı dosyalarla veya tasarımcıda farklı bileşenlerle çalışabilirsiniz. Bu seçenek temizlenirken, Çözüm Gezgini **otomatik** olarak değişmez. Bu seçenek varsayılan olarak etkindir.

## <a name="show-advanced-build-configurations"></a>Gelişmiş derleme yapılandırmalarını gösterme

Bu seçildiğinde, derleme yapılandırma seçenekleri Project **Sayfaları iletişim** kutusunda ve Çözüm Özellik Sayfaları **iletişim kutusunda** görüntülenir. Temizlenince, derleme yapılandırma seçenekleri Project Özellik Sayfaları iletişim kutusunda ve  **bir** yapılandırma veya iki yapılandırma içeren Visual Basic ve C# projeleri için Çözüm Özellik Sayfaları iletişim kutusunda görünmez. Proje kullanıcı tanımlı bir yapılandırmaya sahipse, derleme yapılandırma seçenekleri gösterilir.

Seçimi kaldırıldığında Derleme menüsündeki  Derleme Çözümü, Çözümü Yeniden Derleme ve Çözümü Temizle gibi komutlar Yayın yapılandırmasında ve Hata  Ayıklama menüsünde Hata Ayıklamayı Başlat ve Hata Ayıklama Olmadan Başlat gibi komutlar Hata Ayıklama yapılandırmasında gerçekleştirilir. 

## <a name="always-show-solution"></a>Çözümü her zaman göster

Seçildiğinde, çözüm ve çözümler üzerinde eyleme geçen tüm komutlar her zaman IDE'de gösterilir. Temizlenin, tüm projeler tek başına projeler olarak oluşturulur ve çözümde yalnızca bir proje Çözüm Gezgini IDE'de çözümler üzerinde eyleme geçen komutlarda çözümü görmüyorsunuz.

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>Oluşturulduğunda yeni projeleri kaydetme

Seçildiğinde, Yeni Çalışma Alanı iletişim kutusunda projeniz **için bir Project** belirtebilirsiniz. Temiz olduğunda, tüm yeni projeler geçici projeler olarak oluşturulur. Geçici projelerle çalışırken, disk konumu belirtmek zorunda kalmadan bir proje oluşturabilir ve bu projeyle denemeler oluşturabilirsiniz.

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>Proje konumu güvenilir değilken kullanıcıya uyarı uygulama

Yeni bir proje oluşturmak veya mevcut projeyi tam olarak güvenilir olmayan bir konumda (örneğin, BIR UNC yolunda veya HTTP yolunda) açmaya çalışırken bir ileti görüntülenir. Tam olarak güvenilir bir konumda proje oluşturma veya açma girişiminde bulundurarak iletinin her görüntülendiğinde görüntülendiğinden emin olmak için bu seçeneği kullanın.

## <a name="show-output-window-when-build-starts"></a>Derleme başladığında Çıkış penceresini göster

Çözüm [derlemelerinin başlangıcında](../../ide/reference/output-window.md) IDE'de Çıkış penceresini otomatik olarak görüntüler.

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Dosyaları yeniden görüntülerken sembolik yeniden başlatma istemi

Seçildiğinde, Visual Studio olup olmadığını soran bir ileti kutusu görüntüler. Ayrıca projedeki tüm başvuruları kod öğesi olarak yeniden adlandırması gerekir.

## <a name="prompt-before-moving-files-to-a-new-location"></a>Dosyaları yeni bir konuma taşımadan önce sor

Bu seçildiğinde, Visual Studio konumlarının bir onay iletisi kutusu ile değiştirilemeden önce bir onay iletisi **Çözüm Gezgini.**

## <a name="reopen-documents-on-solution-load"></a>Çözüm yükü üzerinde belgeleri yeniden açma

Seçildiğinde, çözüm kapatılan önceki sefer açık kalan belgeler çözüm açıldığında otomatik olarak açılır.

Belirli dosya veya tasarımcıların yeniden açılması çözüm yüklemesini geciktirebilirsiniz. Çözümün önceki [bağlamını geri yüklemek istemiyorsanız](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) çözüm yükleme performansını geliştirmek için bu seçeneğin işaretini kaldırın.

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>Çözüm Çözüm Gezgini proje hiyerarşisi durumunu geri yükleme

Seçildiğinde, çözümün en son Çözüm Gezgini genişletilen veya daraltılmış olup olmadığıyla ilgili olarak düğümler içinde düğümlerin durumunu geri yükleme. Büyük çözümler için çözüm yükleme sürelerini azaltmak için bu seçeneğin seçimini kaldırın.

> [!TIP]
> Bu seçeneği devre dışı bıraksanız, Çözüm Gezgini araç çubuğunda Etkin Belgeyle Eşitle'yi seçerek etkin belgeye **Çözüm Gezgini** olur. 
>
> ![Çözüm Gezgini'de etkin belgeyle eşitleme](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>SDK stili proje dosyalarını çift tıklamayla veya Enter tuşuyla açma

Bu seçenek seçildiğinde ve Çözüm Gezgini'de SDK stili bir proje düğümüne çift tıklar veya bunu seçin ve **Enter** tuşuna basın. Proje dosyası \* (örneğin, .csproj dosyası) düzenleyicide XML olarak açılır. Seçimi kaldırıldığında, Çözüm Gezgini sdk stili proje düğümüne çift tıklar veya bunu seçerek **Enter** tuşuna basıldığında düğüm genişlet veya daraltılabilir.

Bu seçeneği belirtmiş değilseniz ve SDK stili bir proje dosyasını düzenlemek için, Çözüm Gezgini'de proje düğümüne sağ tıklayın ve Dosyada **Düzenle'Project seçin.** Diğer proje türleri için, projeyi çalışma alanı içinde düzenlemeden önce Visual Studio.

> [!TIP]
> SDK *stili bir proje* veya proje SDK'sı, 15.0 ile birlikte tanıtıldı daha yeni, daha kolaylaştırılmış bir MSBuild biçimine sahiptir. [](../../msbuild/how-to-use-project-sdk.md) SDK stilinde bir proje `Sdk` öğesinde bir öznitelik `Project` içerir, örneğin `<Project Sdk="Microsoft.NET.Sdk">` . Visual Studio şablonlarından birini kullanarak yeni bir .NET Core projesi oluşturursanız sdk Visual Studio proje oluşturabilirsiniz.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler iletişim kutusu: Projeler ve \> Çözümler Konumları](projects-solutions-locations-options.md)
- [Seçenekler İletişim Kutusu, Projeler ve Çözümler, Derleme ve Çalıştırma](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Seçenekler İletişim Kutusu, Projeler ve Çözümler, Web Projeleri](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
