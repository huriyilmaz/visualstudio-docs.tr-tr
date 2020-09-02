---
title: 'Nasıl yapılır: etki alanına özgü dili yeni sürüme geçirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 45f7b38f7dbb6ea470b2d9e186dc8e6bf4b33b1e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657336"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Nasıl yapılır: Etki Alanına Özgü Dili Yeni Sürüme Geçirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs2010](../includes/vs2010-md.md)]İle dağıtılan sürümüne, etki alanına özgü dili tanımlayan ve kullanan projeleri geçirebilirsiniz [!INCLUDE[dsl](../includes/dsl-md.md)] [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] .

 Bir geçiş aracı bir parçası olarak sağlanır [!INCLUDE[vssdk_current_long](../includes/vssdk-current-long-md.md)] . Araç, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanan veya dsl araçlarını tanımlayan projeleri ve çözümleri dönüştürür.

 Geçiş aracını açıkça çalıştırmanız gerekir: ' de bir çözüm açtığınızda bu otomatik olarak başlatılmaz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Araç ve ayrıntılı kılavuz belgesi şu yolda bulunabilir:

 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>DSL projelerinizi geçirmeden önce
 Geçiş Aracı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Proje dosyalarını (**. csproj**) ve çözüm dosyalarını (**. sln**) değiştirir.

#### <a name="to-prepare-projects-for-migration"></a>Projeleri geçişe hazırlamak için.

- **. Csproj** ve **. sln** dosyalarının yazılabilmesini sağlayın. Kaynak denetimi altındaysa, kullanıma aldıklarından emin olun.

- Geçişini planladığınız klasörlerin bir kopyasını oluşturun.

## <a name="migrating-a-collection-of-projects"></a>Proje koleksiyonunu geçirme

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>DSL projelerini ve çözümlerini Visual Studio 2010 ' ye geçirmek için

1. DSL geçiş aracını başlatın.

   - Windows Gezgini 'nde (veya dosya Gezgini) araca çift tıklayarak veya aracı bir komut isteminden başlatabilirsiniz. Araç şu konumda:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Dönüştürmek istediğiniz çözüm ve projeleri içeren bir klasör seçin.

   - Aracın en üstündeki kutuya yolu girin veya **Araştır**' a tıklayın.

     Geçiş Aracı, DSLs 'leri tanımlayan veya kullanan bir proje ağacı görüntüler. Ağaç, **Microsoft. VisualStudio. modellemesi. SDK** veya **textşablon** oluşturma derlemelerini kullanan her projeyi içerir.

3. Proje ağacını gözden geçirin ve dönüştürmek istemediğiniz projelerin işaretini kaldırın.

   - Aracın yapacağız değişikliklerin listesini görmek için bir proje veya çözüm seçin.

       > [!NOTE]
       > Klasör adlarının yanında görünen onay kutularının etkisi yoktur. Projeleri ve çözümleri incelemek için klasörleri genişletmeniz gerekir.

4. Projeleri dönüştürün.

   1. **Dönüştür**'e tıklayın.

        Her proje dosyası dönüştürüldükten sonra _Project._**csproj** 'un bir kopyası _Project_**. VS2008. csproj** olarak kaydedilir

        Her çözümün bir kopyası _solution_**. sln** , _Solution_**. VS2008. sln** olarak kaydedilir

   2. Bildirilen tüm başarısız dönüştürmeleri araştırın.

        Hataların metin penceresinde bildirilmesi. Ayrıca, ağaç görünümünde dönüştürebileceğiniz her düğümde kırmızı bayrak gösterilir. Bu hata hakkında daha fazla bilgi edinmek için düğüme tıklayabilirsiniz.

5. Başarıyla dönüştürülmüş projeler içeren çözümlerdeki **Tüm Şablonları Dönüştür** .

   1. Çözümü açın.

   2. Çözüm Gezgini üstbilgisindeki **Tüm Şablonları Dönüştür** düğmesine tıklayın.

       > [!NOTE]
       > Bu adımı gereksiz hale getirebilirsiniz. Daha fazla bilgi için bkz. [tüm şablonları dönüştürmeyi otomatikleştirme](https://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

6. Dönüştürülen projelerde özel kodunuzu güncelleştirin.

   - Projeleri oluşturmayı deneyin ve tüm sorunları araştırın.

   - Tasarlayıcıyı test edin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Görselleştirme ve modelleme SDK 'daki yenilikler](../misc/what-s-new-in-visualization-and-modeling-sdk.md)
