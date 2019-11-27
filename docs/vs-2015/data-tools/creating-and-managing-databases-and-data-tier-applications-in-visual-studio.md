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
ms.openlocfilehash: c2b1caf45235f9dd745841cb26a2fa10a148a7b5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299646"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Veritabanlarını ve Visual Studio'daki veri katmanı uygulamaları oluşturma ve yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ÖNEMLİ]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] önceki sürümlerinde yer alan veritabanı projeleri artık [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] araçlarında sunulmaktadır. Daha fazla bilgi için bkz. [SQL Server Developer araçları](https://go.microsoft.com/fwlink/?LinkId=228126).

 Veritabanı projeleri yeni veritabanları oluşturmak için kullanabileceğiniz yeni veri katmanı uygulamaları (Dac'ler) ve var olan veritabanlarını ve veri katmanı uygulamaları güncelleştirmek için. Hem veritabanı projeleri hem de DAC projeleri çok yönetilen veya yerel kod için bu teknikler uyguladığınız aynı şekilde, veritabanı geliştirme çalışmalarınızda kullanmanız için sürüm denetimi ve proje yönetimi teknikleri uygulanmasını sağlar. Bir *DAC projesi*, *veritabanı projesi*veya *sunucu projesi* oluşturarak ve sürüm denetimi altına koyarak, geliştirme takımınızın veritabanlarına ve veritabanı sunucularına yapılan değişiklikleri yönetmesine yardımcı olabilirsiniz. Ekibinizin üyeleri, takım ile paylaşmadan önce, *yalıtılmış bir geliştirme ortamında*veya korumalı alanda değişiklik yapmak, derlemek ve test etmek için dosyaları kullanıma alabilir. Kod kalitesinin sağlanmasına yardımcı olmak için takımınızın tamamlayın ve değişiklikleri üretime dağıtmadan önce tüm değişiklikleri veritabanını belirli bir sürümü için bir hazırlama ortamında test.

 Veri katmanı uygulamaları tarafından desteklenen veritabanı özelliklerinin bir listesi için bkz. Microsoft Web sitesindeki [veri katmanı uygulamalarında desteklenen özellikler](https://go.microsoft.com/fwlink/?LinkId=164239) . Veri katmanı uygulamaları tarafından desteklenmeyen özellikleri veritabanınızdaki kullanırsanız, veritabanınıza değişiklikleri yönetmek için bunun yerine bir veritabanı projesi kullanmanız gerekir.

## <a name="common-high-level-tasks"></a>Ortak bir üst düzey görevler

|Üst düzey görev|Destekleyici İçerik|
|----------------------|------------------------|
|**Veri katmanı uygulamasının geliştirilmesini başlatın:** DAC, bir [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] veritabanının tanımını ve bir istemci-sunucu veya 3 katmanlı uygulama tarafından kullanılan destekleyici örnek nesnelerini içeren [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] ile sunulan yeni bir kavramdır. Bir DAC, tablolar ve görünümler, oturum açma bilgileri gibi örnek varlıkları birlikte gibi nesneleri içerir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kullanarak bir DAC projesi oluşturabilir, bir DAC paket dosyası oluşturabilir ve bu DAC paket dosyasını, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] veritabanı altyapısının bir örneğine dağıtım için bir veritabanı yöneticisine gönderebilirsiniz.|-   [veri katmanı uygulamaları oluşturma ve yönetme](https://go.microsoft.com/fwlink/?LinkId=160741) (Microsoft Web sitesi)<br />-   [SQL Server Management Studio](https://go.microsoft.com/fwlink/?LinkId=227328)|
|**Yinelemeli veritabanı geliştirme gerçekleştiriliyor:** Bir geliştirici veya test edici iseniz, projenin bölümlerine göz atın ve ardından bunları yalıtılmış bir geliştirme ortamında güncelleştirebilirsiniz. Bu ortam türünü kullanarak, diğer takım üyeleri etkilemeden değişikliklerinizi test edebilirsiniz. Değişiklik tamamlandıktan sonra burada diğer takım üyelerinin yaptığınız değişiklikleri alabilir ve yapı ve bunları bir test sunucusuna dağıtmak geri sürüm denetimine, dosyaları denetleyin.|[sorgu ve metin düzenleyicileri -   (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft Web sitesi)<br />-   [Transact-SQL hata ayıklayıcı](https://go.microsoft.com/fwlink/?LinkId=227324) (Microsoft Web sitesi)|
|**Prototip oluşturma, test sonuçlarını doğrulama ve veritabanı komut dosyalarını ve nesnelerini değiştirme:** [!INCLUDE[tsql](../includes/tsql-md.md)] düzenleyicisini kullanarak bu ortak görevlerden herhangi birini gerçekleştirebilirsiniz.|[sorgu ve metin düzenleyicileri -   (SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft Web sitesi)|

## <a name="see-also"></a>Ayrıca Bkz.
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
