---
title: Veritabanları ve veri katmanı uygulamaları oluşturma ve yönetme
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b793789e092b46f14db397c1f8aef4e98544f856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851691"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Visual Studio'da veritabanları ve veri katmanı uygulamaları oluşturma ve yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ÖNEMLI
> Daha önceki sürümlerinde bulunan veritabanı projeleri [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] artık Araçlar 'da sunulmaktadır [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] . Daha fazla bilgi için bkz. [SQL Server Developer araçları](https://msdn.microsoft.com/library/hh272686(VS.103).aspx).

 Veritabanı projelerini kullanarak yeni veritabanları, yeni veri katmanı uygulamaları (PACS) oluşturabilir ve mevcut veritabanlarını ve veri katmanı uygulamalarını güncelleştirebilirsiniz. Hem veritabanı projeleri hem de DAC projeleri, bu teknikleri yönetilen veya yerel koda uyguladığınız şekilde veritabanı geliştirme çabalarınıza sürüm denetimi ve proje yönetimi teknikleri uygulamanızı sağlar. Bir *DAC projesi*, *veritabanı projesi*veya *sunucu projesi* oluşturarak ve sürüm denetimi altına koyarak, geliştirme takımınızın veritabanlarına ve veritabanı sunucularına yapılan değişiklikleri yönetmesine yardımcı olabilirsiniz. Ekibinizin üyeleri, takım ile paylaşmadan önce, *yalıtılmış bir geliştirme ortamında*veya korumalı alanda değişiklik yapmak, derlemek ve test etmek için dosyaları kullanıma alabilir. Kod kalitesinin sağlanmasına yardımcı olmak için ekibiniz, değişiklikleri üretime dağıtmadan önce hazırlama ortamında veritabanının belirli bir sürümüne yönelik tüm değişiklikleri bitirebilmeniz ve test edebilir.

 Veri katmanı uygulamaları tarafından desteklenen veritabanı özelliklerinin bir listesi için bkz. Microsoft Web sitesindeki [veri katmanı uygulamalarında desteklenen özellikler](https://msdn.microsoft.com/library/ee362013(VS.100).aspx) . Veritabanınızda veri katmanı uygulamaları tarafından desteklenmeyen özellikler kullanıyorsanız, veritabanınızdaki değişiklikleri yönetmek için bir veritabanı projesi kullanmanız gerekir.

## <a name="common-high-level-tasks"></a>Ortak üst düzey görevler

|Üst düzey görev|Destekleyici İçerik|
|----------------------|------------------------|
|**Veri katmanı uygulamasının geliştirilmesini başlatın:** DAC, bir [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] veritabanı tanımını ve bir istemci-sunucu veya 3 katmanlı uygulama tarafından kullanılan destekleyici örnek nesneleri içeren ile sunulan yeni bir kavramdır. DAC, tablolar ve görünümler gibi veritabanı nesnelerini, örneğin oturum açma işlemleri gibi örnek varlıklarla birlikte içerir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]' I kullanarak BIR DAC projesi oluşturabilir, BIR dac paket dosyası oluşturabilir ve bu dac paket dosyasını veritabanı altyapısının bir örneğine dağıtım için bir veritabanı yöneticisine gönderebilirsiniz [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-   [Veri katmanı uygulamaları oluşturma ve yönetme](https://msdn.microsoft.com/library/ee361996(VS.100).aspx) (Microsoft Web sitesi)<br />-   [SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(SQL.110).aspx)|
|**Yinelemeli veritabanı geliştirme gerçekleştiriliyor:** Bir geliştirici veya test edici iseniz, projenin bölümlerine göz atın ve ardından bunları yalıtılmış bir geliştirme ortamında güncelleştirebilirsiniz. Bu ortam türünü kullanarak, ekibinizin diğer üyelerini etkilemeden değişikliklerinizi test edebilirsiniz. Değişiklikler tamamlandıktan sonra, diğer ekip üyelerinin değişiklikleri alabileceği ve bunları bir test sunucusuna dağıtabeceği sürüm denetimine geri döndüğünüzde dosyaları kontrol edersiniz.|-   [Sorgu ve metin düzenleyicileri (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (Microsoft Web sitesi)<br />-   [Transact-SQL hata ayıklayıcı](https://msdn.microsoft.com/library/cc645997(SQL.110).aspx) (Microsoft Web sitesi)|
|**Prototip oluşturma, test sonuçlarını doğrulama ve veritabanı komut dosyalarını ve nesnelerini değiştirme:** [!INCLUDE[tsql](../includes/tsql-md.md)] Bu ortak görevlerden herhangi birini gerçekleştirmek için düzenleyiciyi kullanabilirsiniz.|-   [Sorgu ve metin düzenleyicileri (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (Microsoft Web sitesi)|

## <a name="see-also"></a>Ayrıca Bkz.
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
