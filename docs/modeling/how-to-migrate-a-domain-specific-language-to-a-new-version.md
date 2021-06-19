---
title: 'Nasıl yapılır: Domain-Specific dil projesi geçirme'
description: Bir etki alanına özgü dil projesinin Visual Studio 'nun daha yeni bir sürümüne nasıl geçirileceğiyle ilgili bilgi sağlar.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 8119f465e32d3754dc446524286e0a2c12dedc40
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387196"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Nasıl yapılır: Etki Alanına Özgü Dili Yeni Sürüme Geçirme
[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]İle dağıtılan sürümüne, etki alanına özgü dili tanımlayan ve kullanan projeleri geçirebilirsiniz [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] .

 Bir geçiş aracı bir parçası olarak sağlanır [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] . Araç, DSL araçlarını kullanan veya tanımlayan Visual Studio projelerini ve çözümlerini dönüştürür.

 Geçiş aracını açıkça çalıştırmanız gerekir: Visual Studio 'da bir çözüm açtığınızda bu otomatik olarak başlatılmaz. Araç ve ayrıntılı kılavuz belgesi şu yolda bulunabilir:

 **% Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>DSL projelerinizi geçirmeden önce
 Geçiş Aracı, Visual Studio proje dosyalarını (**. csproj**) ve çözüm dosyalarını (**. sln**) değiştirir.

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

        Her çözümün bir kopyası **. sln** , _Solution_**. VS2008. sln** olarak kaydedilir

   2. Bildirilen tüm başarısız dönüştürmeleri araştırın.

        Hataların metin penceresinde bildirilmesi. Ayrıca, ağaç görünümünde dönüştürebileceğiniz her düğümde kırmızı bayrak gösterilir. Bu hata hakkında daha fazla bilgi edinmek için düğüme tıklayabilirsiniz.

5. Başarıyla dönüştürülmüş projeler içeren çözümlerdeki **Tüm Şablonları Dönüştür** .

   1. Çözümü açın.

   2. Çözüm Gezgini üstbilgisindeki **Tüm Şablonları Dönüştür** düğmesine tıklayın.

       > [!NOTE]
       > Bu adımı gereksiz hale getirebilirsiniz. Daha fazla bilgi için bkz. [tüm şablonları dönüştürmeyi otomatikleştirme](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

6. Dönüştürülen projelerde özel kodunuzu güncelleştirin.

   - Projeleri oluşturmayı deneyin ve tüm sorunları araştırın.

   - Tasarlayıcıyı test edin.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [İlgili blog gönderileri](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)