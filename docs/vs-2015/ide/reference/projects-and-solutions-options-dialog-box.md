---
title: Projeler ve çözümler, Seçenekler Iletişim kutusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 245b453a3020e79b924cb8058ff392bd59673402
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662130"
---
# <a name="projects-and-solutions-options-dialog-box"></a>Projeler ve Çözümler, Seçenekler İletişim Kutusu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Proje klasörlerinin varsayılan yolunu ayarlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ve proje geliştirilip derlendikleri Için **Çıkış** penceresinin, **görev listesi**ve **Çözüm Gezgini** varsayılan davranışını belirler. Bu iletişim kutusuna erişmek için **Araçlar/Seçenekler** ' i **ve ardından projeler ve çözümler**' i genişletin ve **genel**' i tıklatın

> [!NOTE]
> İletişim kutularında kullanılabilen seçenekler ve gördüğünüz menü komutlarının adları ve konumları, etkin ayarlarınıza veya sürümüne bağlı olarak yardım altında açıklananlar arasından farklılık gösterebilir. Bu yardım sayfası, **genel geliştirme ayarları** göz önünde bulundurularak yazılmıştır. Ayarlarınızı görüntülemek veya değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Ayarlar
 **Proje konumu** Yeni projelerin ve çözüm klasörlerinin ve dizinlerin oluşturulduğu varsayılan konumu ayarlar. Birçok iletişim kutusu ayrıca klasör başlangıç noktaları için bu seçenekte ayarlanan konumu kullanır. Örneğin, proje Aç iletişim kutusu, projem kısayolu için bu konumu kullanır.

 **Kullanıcı projesi şablonlarının konumu** **Şablonlarım**listesini oluşturmak Için **Yeni proje** iletişim kutusu tarafından kullanılan varsayılan konumu ayarlar. Daha fazla bilgi için bkz. [nasıl yapılır: şablonları bulma ve düzenleme](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

 **Kullanıcı öğesi şablonlarının konumu** **Şablonlarım**listesini oluşturmak Için **Yeni öğe Ekle** iletişim kutusu tarafından kullanılan varsayılan konumu ayarlar. Daha fazla bilgi için bkz. [nasıl yapılır: şablonları bulma ve düzenleme](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

 **Derleme hatalarla sonlandıysanız her zaman hata listesi göster** Yapı tamamlamada **hata listesi** penceresini açar, yalnızca bir proje derlenbir şekilde başarısız olursa. Oluşturma işlemi sırasında oluşan hatalar görüntülenir. Bu seçenek kaldırıldığında hatalar yine oluşur ancak yapı tamamlandığında pencere açılmaz. Bu seçenek varsayılan olarak etkindir.

 **Çözüm Gezgini etkin öğeyi izle** Seçildiğinde, **Çözüm Gezgini** otomatik olarak açılır ve etkin öğe seçilir. Seçilen öğe, bir proje veya çözümde farklı dosyalarla veya bir tasarımcıda farklı bileşenlere çalışırken değişir. Bu seçenek temizlenmiş olduğunda **Çözüm Gezgini** seçimi otomatik olarak değişmez. Bu seçenek varsayılan olarak etkindir.

 **Gelişmiş derleme yapılandırmasını göster** Seçildiğinde, derleme yapılandırma seçenekleri **Proje özellik sayfaları** iletişim kutusunda ve **Çözüm Özellik sayfaları** iletişim kutusunda görünür. Temizlenme sırasında, derleme yapılandırma seçenekleri **Proje özellik sayfaları** iletişim kutusunda ve bir yapılandırma ya da iki yapılandırma hata ayıklaması ve sürümü içeren projeler Için **Çözüm Özellik sayfaları** iletişim kutusunda görünmez [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] . Bir projede Kullanıcı tanımlı bir yapılandırma varsa, derleme yapılandırma seçenekleri gösterilir.

 Seçilmediğinde, oluşturma **çözümü**, **çözümü yeniden oluşturma**ve **çözümü Temizleme**gibi **derleme** menüsündeki komutlar, sürüm yapılandırması üzerinde gerçekleştirilir ve hata **ayıklamayı Başlat** ve hata ayıklama **olmadan Başlat**gibi **hata** ayıklama menüsündeki komutlar hata ayıklama yapılandırmasında gerçekleştirilir.

 **Çözümü her zaman göster** Seçildiğinde, çözüm ve çözümler üzerinde işlem yapan tüm komutlar her zaman IDE 'de gösterilir. Temizlenme sırasında, tüm projeler tek başına projeler olarak oluşturulur ve çözüm yalnızca bir proje içeriyorsa IDE 'deki çözümler üzerinde çalışan Çözüm Gezgini veya komutlarda çözümü görmezsiniz.

 **Oluşturulduğunda yeni projeleri kaydet** Seçildiğinde, **Yeni proje** iletişim kutusunda projeniz için bir konum belirtebilirsiniz. Kaldırıldığında, tüm yeni projeler geçici proje olarak oluşturulur. Geçici projelerle çalışırken bir disk konumu belirtmek zorunda kalmadan bir proje oluşturup deneyebilirsiniz.

 **Proje konumu güvenilir olmadığında kullanıcıyı uyar** Yeni bir proje oluşturmaya veya var olan bir projeyi tam güvenilir olmayan bir konumda açmaya çalışırsanız (örneğin, bir UNC yolu veya HTTP yolu üzerinde), bir ileti görüntülenir. Tam güvenilir olmayan bir konumda bir projeyi oluşturma veya açma girişiminde bulunan her seferinde iletinin görüntülenip görüntülenmeyeceğini belirtmek için bu seçeneği kullanın.

 **Derleme başladığında çıkış penceresini göster** , Çıkış Penceresi otomatik olarak IDE 'de çözüm yapıları kümesinden görüntüler. Daha fazla bilgi için bkz. [nasıl yapılır: denetim çıkış penceresi](https://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858). Bu seçenek varsayılan olarak etkindir.

 **Dosyaları yeniden adlandırırken sembolik yeniden adlandırma iste** Seçildiğinde, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projedeki tüm başvuruları kod öğesine de yeniden adlandırmayacağını soran bir ileti kutusu görüntüler.

## <a name="see-also"></a>Ayrıca Bkz.
 [Seçenekler Iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
