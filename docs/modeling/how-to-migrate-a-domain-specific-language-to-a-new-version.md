---
title: 'Nasıl yapılır: Domain-Specific Language projesini geçirme'
description: Etki alanına özgü dil projesini, etki alanına özgü dil projesinin daha yeni bir sürümüne geçirme hakkında Visual Studio.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: bf568d319fad994746cdee7eb9554f88304b4878
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061239"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Nasıl yapılır: Etki Alanına Özgü Dili Yeni Sürüme Geçirme
Etki alanına özgü dili tanımlayan ve kullanan projeleri ile dağıtılan [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] sürümünden [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] sürümüne [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] geçirebilirsiniz.

 bir geçiş aracı, 'nin bir parçası olarak [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] sağlanır. Araç, DSL Visual Studio kullanan veya tanımlayan projeleri ve çözümleri dönüştürür.

 Geçiş aracını açıkça çalıştırmalı ve çözümde bir çözüm Visual Studio. Araç ve ayrıntılı kılavuz belgesi şu yolda bulunabilir:

 **%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

## <a name="before-you-migrate-your-dsl-projects"></a>DSL Projelerinizi Geçirmeden Önce
 Geçiş aracı, proje Visual Studio (**.csproj**) ve çözüm dosyalarını (**.sln**) değiştiren bir araçtır.

#### <a name="to-prepare-projects-for-migration"></a>Projeleri geçişe hazırlamak için.

- **.csproj ve** **.sln dosyalarının** yazılaa olduğundan emin olun. Kaynak denetimi altındalarsa kullanıma alınmış olduğundan emin olun.

- Geçirmek istediğiniz klasörlerin bir kopyasını oluşturun.

## <a name="migrating-a-collection-of-projects"></a>Proje Koleksiyonunun Nasıl Geçirdiklerini

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>DSL Projelerini ve Çözümlerini Visual Studio 2010'a Geçirme

1. DSL Geçiş Aracı'nı başlatma.

   - Araç Gezgini'nde (Windows veya Dosya Gezgini) çift tıklar veya bir komut isteminden aracı başlatabilirsiniz. Araç şu konumdadır:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Dönüştürmek istediğiniz çözümleri ve projeleri içeren bir klasör seçin.

   - Aracın üst kısmında yer alan kutuya yolu girin veya Gözat'a **tıklayın.**

     Geçiş aracı, DSL'leri tanımlayan veya kullanan projelerin ağacını görüntüler. Ağaç, **Microsoft.VisualStudio.Modeling.Sdk** veya **TextTemplating derlemelerini kullanan her projeyi** içerir.

3. Proje ağacını gözden geçirin ve dönüştürmek istediğiniz projelerin işaretini kaldırın.

   - Aracın yapacakları değişikliklerin listesini görmek için bir proje veya çözüm seçin.

       > [!NOTE]
       > Klasör adlarının yanında görünen onay kutularının hiçbir etkisi yoktur. Projeleri ve çözümleri incelemek için klasörleri genişletmelisiniz.

4. Projeleri dönüştürme.

   1. **Dönüştür**'e tıklayın.

        Her proje dosyası dönüştürülmeden önce .**csproj** projesinin bir kopyası **.vs2008.csproj projesi olarak kaydedilir**

        **.sln** _çözümünün_ bir kopyası çözüm **.vs2008.sln olarak kaydedilir**

   2. Bildirilen başarısız dönüştürmeleri araştır.

        Hatalar metin penceresinde raporlandı. Buna ek olarak, ağaç görünümü dönüştürülemedi her düğümde kırmızı bir bayrak gösterir. Bu hata hakkında daha fazla bilgi almak için düğüme tıklarsiniz.

5. **Başarıyla dönüştürülen** projeleri içeren çözümlerde Tüm Şablonları Dönüştür.

   1. Çözümü açın.

   2. Uygulamanın **üst bilgisinde** Tüm Şablonları Dönüştür düğmesine Çözüm Gezgini.

       > [!NOTE]
       > Bu adımı gereksiz hale de 3. Daha fazla bilgi için [bkz. How to Automate Transform All Templates](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

6. Dönüştürülen projelerde özel kodunuzu güncelleştirin.

   - Projeleri derlemeyi ve hataları araştırmayı deneme.

   - Tasarımcınızı test etmek.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [İlgili blog gönderileri](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)