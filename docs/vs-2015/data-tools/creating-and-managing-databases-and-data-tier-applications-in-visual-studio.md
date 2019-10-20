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
ms.openlocfilehash: 2d6ed13f2e21ea6b9da82eb47afefdd16088e71d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672481"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Visual Studio'da veritabanları ve veri katmanı uygulamaları oluşturma ve yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ÖNEMLI
> @No__t_0 önceki sürümlerinde yer alan veritabanı projeleri artık [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] araçlarında sunulmaktadır. Daha fazla bilgi için bkz. [SQL Server Developer araçları](http://go.microsoft.com/fwlink/?LinkId=228126).

 Veritabanı projelerini kullanarak yeni veritabanları, yeni veri katmanı uygulamaları (PACS) oluşturabilir ve mevcut veritabanlarını ve veri katmanı uygulamalarını güncelleştirebilirsiniz. Hem veritabanı projeleri hem de DAC projeleri, bu teknikleri yönetilen veya yerel koda uyguladığınız şekilde veritabanı geliştirme çabalarınıza sürüm denetimi ve proje yönetimi teknikleri uygulamanızı sağlar. Bir *DAC projesi*, *veritabanı projesi*veya *sunucu projesi* oluşturarak ve sürüm denetimi altına koyarak, geliştirme takımınızın veritabanlarına ve veritabanı sunucularına yapılan değişiklikleri yönetmesine yardımcı olabilirsiniz. Ekibinizin üyeleri, takım ile paylaşmadan önce, *yalıtılmış bir geliştirme ortamında*veya korumalı alanda değişiklik yapmak, derlemek ve test etmek için dosyaları kullanıma alabilir. Kod kalitesinin sağlanmasına yardımcı olmak için ekibiniz, değişiklikleri üretime dağıtmadan önce hazırlama ortamında veritabanının belirli bir sürümüne yönelik tüm değişiklikleri bitirebilmeniz ve test edebilir.

 Veri katmanı uygulamaları tarafından desteklenen veritabanı özelliklerinin bir listesi için bkz. Microsoft Web sitesindeki [veri katmanı uygulamalarında desteklenen özellikler](http://go.microsoft.com/fwlink/?LinkId=164239) . Veritabanınızda veri katmanı uygulamaları tarafından desteklenmeyen özellikler kullanıyorsanız, veritabanınızdaki değişiklikleri yönetmek için bir veritabanı projesi kullanmanız gerekir.

## <a name="common-high-level-tasks"></a>Ortak üst düzey görevler

|Üst düzey görev|Destekleyici İçerik|
|----------------------|------------------------|
|**Veri katmanı uygulamasının geliştirilmesini başlatın:** DAC, bir [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] veritabanının tanımını ve bir istemci-sunucu veya 3 katmanlı uygulama tarafından kullanılan destekleyici örnek nesnelerini içeren [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] ile sunulan yeni bir kavramdır. DAC, tablolar ve görünümler gibi veritabanı nesnelerini, örneğin oturum açma işlemleri gibi örnek varlıklarla birlikte içerir. @No__t_0 kullanarak bir DAC projesi oluşturabilir, bir DAC paket dosyası oluşturabilir ve bu DAC paket dosyasını, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] veritabanı altyapısının bir örneğine dağıtım için bir veritabanı yöneticisine gönderebilirsiniz.|-   [veri katmanı uygulamaları oluşturma ve yönetme](http://go.microsoft.com/fwlink/?LinkId=160741) (Microsoft Web sitesi)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**Yinelemeli veritabanı geliştirme gerçekleştiriliyor:** Bir geliştirici veya test edici iseniz, projenin bölümlerine göz atın ve ardından bunları yalıtılmış bir geliştirme ortamında güncelleştirebilirsiniz. Bu ortam türünü kullanarak, ekibinizin diğer üyelerini etkilemeden değişikliklerinizi test edebilirsiniz. Değişiklikler tamamlandıktan sonra, diğer ekip üyelerinin değişiklikleri alabileceği ve bunları bir test sunucusuna dağıtabeceği sürüm denetimine geri döndüğünüzde dosyaları kontrol edersiniz.|[sorgu ve metin düzenleyicileri -    (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft Web sitesi)<br />-   [Transact-SQL hata ayıklayıcı](http://go.microsoft.com/fwlink/?LinkId=227324) (Microsoft Web sitesi)|
|**Prototip oluşturma, test sonuçlarını doğrulama ve veritabanı komut dosyalarını ve nesnelerini değiştirme:** @No__t_1 düzenleyicisini kullanarak bu ortak görevlerden herhangi birini gerçekleştirebilirsiniz.|[sorgu ve metin düzenleyicileri -    (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (Microsoft Web sitesi)|

## <a name="see-also"></a>Ayrıca Bkz.
 [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
