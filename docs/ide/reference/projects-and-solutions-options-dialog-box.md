---
title: Projeler ve çözümler, Seçenekler iletişim kutusu
description: Projeler ve çözümlerle ilgili Visual Studio davranışını tanımlamak için projeler ve çözümler bölümünde Genel sayfasını nasıl kullanacağınızı öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: 2fab59a590b59452362a47d48bcdfa7dd8661f57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907506"
---
# <a name="options-dialog-box-projects-and-solutions--general"></a>Seçenekler iletişim kutusu: projeler ve çözümler \> genel

Visual Studio 'nun projelerle ve çözümlerle ilgili davranışını tanımlamak için bu sayfayı kullanın. Bu seçeneklere erişmek için **Araçlar**  >  **Seçenekler**, **Projeler ve çözümler**' i seçin ve ardından **genel**' i seçin.

**Genel** sayfasında aşağıdaki seçenekler bulunur.

## <a name="always-show-error-list-if-build-finishes-with-errors"></a>Derleme hatalarla sonlandıysanız her zaman Hata Listesi göster

Yapı tamamlamada **hata listesi** penceresini açar, yalnızca bir proje derlenbir şekilde başarısız olursa. Oluşturma işlemi sırasında oluşan hatalar görüntülenir. Bu seçenek kaldırıldığında hatalar yine oluşur ancak yapı tamamlandığında pencere açılmaz. Bu seçenek varsayılan olarak etkindir.

## <a name="track-active-item-in-solution-explorer"></a>Çözüm Gezgini etkin öğeyi izle

Seçildiğinde, **Çözüm Gezgini** otomatik olarak açılır ve etkin öğe seçilir. Seçilen öğe, bir proje veya çözümde farklı dosyalarla veya bir tasarımcıda farklı bileşenlere çalışırken değişir. Bu seçenek temizlenmiş olduğunda **Çözüm Gezgini** seçimi otomatik olarak değişmez. Bu seçenek varsayılan olarak etkindir.

## <a name="show-advanced-build-configurations"></a>Gelişmiş derleme yapılandırmasını göster

Seçildiğinde, derleme yapılandırma seçenekleri **Proje özellik sayfaları** iletişim kutusunda ve **Çözüm Özellik sayfaları** iletişim kutusunda görünür. Temizlenme sırasında, derleme yapılandırma seçenekleri **Proje özellik sayfaları** iletişim kutusunda ve bir yapılandırma ya da iki yapılandırma hata ayıklaması ve sürümü içeren Visual Basic ve C# projelerinin **Çözüm Özellik sayfaları** iletişim kutusunda görünmez. Bir projede Kullanıcı tanımlı bir yapılandırma varsa, derleme yapılandırma seçenekleri gösterilir.

Seçilmediğinde, oluşturma **çözümü**, **çözümü yeniden oluşturma** ve **çözümü Temizleme** gibi **derleme** menüsündeki komutlar, sürüm yapılandırması üzerinde gerçekleştirilir ve hata **ayıklamayı Başlat** ve hata ayıklama **olmadan Başlat** gibi **hata** ayıklama menüsündeki komutlar hata ayıklama yapılandırmasında gerçekleştirilir.

## <a name="always-show-solution"></a>Çözümü her zaman göster

Seçildiğinde, çözüm ve çözümler üzerinde işlem yapan tüm komutlar her zaman IDE 'de gösterilir. Temizlenme sırasında, tüm projeler tek başına projeler olarak oluşturulur ve çözüm yalnızca bir proje içeriyorsa IDE 'deki çözümler üzerinde çalışan Çözüm Gezgini veya komutlarda çözümü görmezsiniz.

::: moniker range="vs-2017"

## <a name="save-new-projects-when-created"></a>Oluşturulduğunda yeni projeleri Kaydet

Seçildiğinde, **Yeni proje** iletişim kutusunda projeniz için bir konum belirtebilirsiniz. Kaldırıldığında, tüm yeni projeler geçici proje olarak oluşturulur. Geçici projelerle çalışırken bir disk konumu belirtmek zorunda kalmadan bir proje oluşturup deneyebilirsiniz.

::: moniker-end

## <a name="warn-user-when-the-project-location-is-not-trusted"></a>Proje konumu güvenilir olmadığında kullanıcıyı uyar

Yeni bir proje oluşturmaya veya var olan bir projeyi tam güvenilir olmayan bir konumda açmaya çalışırsanız (örneğin, bir UNC yolu veya HTTP yolu üzerinde), bir ileti görüntülenir. Tam güvenilir olmayan bir konumda bir projeyi oluşturma veya açma girişiminde bulunan her seferinde iletinin görüntülenip görüntülenmeyeceğini belirtmek için bu seçeneği kullanın.

## <a name="show-output-window-when-build-starts"></a>Derleme başladığında çıkış penceresini göster

, [Çıkış penceresini](../../ide/reference/output-window.md) otomatik olarak IDE 'de, çözüm derlemelerinin bilinemeyebilir öğesinde görüntüler.

## <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Dosyaları yeniden adlandırırken sembolik yeniden adlandırma iste

Seçildiğinde, Visual Studio projedeki tüm başvuruları kod öğesine de yeniden adlandırmasının gerekip gerekmediğini soran bir ileti kutusu görüntüler.

## <a name="prompt-before-moving-files-to-a-new-location"></a>Dosyaları yeni bir konuma taşımadan önce sor

Seçildiğinde, dosya konumları **Çözüm Gezgini** eylemler tarafından değiştirilmeden önce Visual Studio bir onay iletisi kutusu görüntüler.

## <a name="reopen-documents-on-solution-load"></a>Çözüm yükünden belgeleri yeniden aç

Seçildiğinde, çözüm açıldığında kalan bir önceki sefer açık olan belgeler otomatik olarak açılır.

Belirli dosya veya tasarımcı türlerini yeniden açmak çözüm yükünü geciktirebilirler. Çözümün önceki bağlamını geri yüklemek istemiyorsanız [çözüm yükleme performansını artırmak](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) için bu seçeneğin işaretini kaldırın.

::: moniker range=">=vs-2019"

## <a name="restore-solution-explorer-project-hierarchy-state-on-solution-load"></a>Çözüm yükünden Çözüm Gezgini proje hiyerarşisi durumunu geri yükle

Seçildiğinde, Çözüm Gezgini düğümlerin durumunu, çözümün en son açılışında genişletilmekte veya daraltılıp daraltıldıklarından bağımsız olarak geri yükler. Büyük çözümler için çözüm yükleme süresini azaltmak üzere bu seçeneğin seçimini kaldırın.

> [!TIP]
> Bu seçeneği devre dışı bırakırsanız, Çözüm Gezgini ' deki etkin belgeye gitmek için kolay bir yol **Çözüm Gezgini** araç çubuğunda **etkin belge ile Eşitle** ' yi seçmektir.
>
> ![Çözüm Gezgini etkin belge ile Eşitle](media/sync-active-document.png)

## <a name="open-sdk-style-project-files-with-double-click-or-the-enter-key"></a>Çift tıklama veya ENTER tuşu ile SDK stili proje dosyaları açın

Bu seçenek belirlendiğinde ve Çözüm Gezgini bir SDK stili proje düğümüne çift tıkladığınızda veya seçin ve ardından **ENTER** tuşuna basarsanız proje dosyası (örneğin, \* . csproj dosyası) düzenleyicide XML olarak açılır. Seçimi kaldırıldığında, Çözüm Gezgini bir SDK stili proje düğümüne çift tıklayarak veya onu seçip **ENTER** tuşuna basarak yalnızca düğümü genişletme veya daraltma etkisi vardır.

Bu seçenek seçilmezse ve bir SDK stili proje dosyasını düzenlemek istiyorsanız, Çözüm Gezgini ' de proje düğümüne sağ tıklayın ve **Proje dosyasını Düzenle**' yi seçin. Diğer proje türleri için öncelikle projeyi Visual Studio 'da düzenlemeden önce kaldırmanız gerekir.

> [!TIP]
> *SDK stili bir proje* veya [Proje SDK](../../msbuild/how-to-use-project-sdk.md)'sı, MSBuild 15,0 ile tanıtılan daha yeni, daha kolay bir proje dosyası biçimine sahiptir. SDK stili bir proje `Sdk` , öğe üzerinde bir özniteliği içerir `Project` , örneğin `<Project Sdk="Microsoft.NET.Sdk">` . Visual Studio şablonlarından yeni bir .NET Core projesi oluşturduğunuzda Visual Studio bir SDK stili proje oluşturur, örneğin.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler iletişim kutusu: projeler ve çözüm \> konumları](projects-solutions-locations-options.md)
- [Seçenekler İletişim Kutusu, Projeler ve Çözümler, Derleme ve Çalıştırma](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Seçenekler İletişim Kutusu, Projeler ve Çözümler, Web Projeleri](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
