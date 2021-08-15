---
title: Veritabanı projeleri ve DAC projeleri
description: Veritabanı projeleri ve veri katmanı uygulamaları (BACS) hakkında bilgi edinin. VERITABANı projelerini kullanarak yeni veritabanları oluşturun, yeni bir Kacs oluşturun ve var olan veritabanlarını güncelleştirin.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9eb21f68e3f843d4d05ef046dfc7de4c01ff5d12053cf8063eb4f805286fb050
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347434"
---
# <a name="database-projects-and-data-tier-applications"></a>Veritabanı projeleri ve veri katmanı uygulamaları

Veritabanı projelerini kullanarak yeni veritabanları, yeni veri katmanı uygulamaları (PACS) oluşturabilir ve mevcut veritabanlarını ve veri katmanı uygulamalarını güncelleştirebilirsiniz. Hem veritabanı projeleri hem de DAC projeleri, bu teknikleri yönetilen veya yerel koda uyguladığınız şekilde veritabanı geliştirme çabalarınıza sürüm denetimi ve proje yönetimi teknikleri uygulamanızı sağlar. Bir DAC projesi, veritabanı projesi veya sunucu projesi oluşturarak ve sürüm denetimi altına koyarak, geliştirme takımınızın veritabanlarına ve veritabanı sunucularına yapılan değişiklikleri yönetmesine yardımcı olabilirsiniz. Ekibinizin üyeleri, takım ile paylaşmadan önce, yalıtılmış bir geliştirme ortamında veya korumalı alanda değişiklik yapmak, derlemek ve test etmek için dosyaları kullanıma alabilir. Kod kalitesinin sağlanmasına yardımcı olmak için ekibiniz, değişiklikleri üretime dağıtmadan önce hazırlama ortamında veritabanının belirli bir sürümüne yönelik tüm değişiklikleri bitirebilmeniz ve test edebilir.

veri katmanı uygulamaları tarafından desteklenen veritabanı özelliklerinin bir listesi için bkz. [SQL Server nesneleri için DAC desteği](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Veritabanınızda veri katmanı uygulamaları tarafından desteklenmeyen özellikler kullanıyorsanız, veritabanınızdaki değişiklikleri yönetmek için bir veritabanı projesi kullanmanız gerekir.

## <a name="common-high-level-tasks"></a>Ortak üst düzey görevler

| High-Level görev | Destekleyici İçerik |
| - | - |
| **Veri katmanı uygulamasının geliştirilmesini başlatın:** veri katmanı uygulaması (DAC) kavramı SQL Server 2008 ile tanıtılmıştı. DAC bir SQL Server veritabanının tanımını ve bir istemci-sunucu veya 3 katmanlı uygulama tarafından kullanılan destekleyici örnek nesnelerini içerir. DAC, tablolar ve görünümler gibi veritabanı nesnelerini, örneğin oturum açma işlemleri gibi örnek varlıklarla birlikte içerir. Visual Studio kullanarak bir dac projesi oluşturabilir, bir dac paket dosyası oluşturabilir ve SQL Server veritabanı altyapısının bir örneğine dağıtım için dac paket dosyasını bir veritabanı yöneticisine gönderebilirsiniz. | - [Veri katmanı uygulamaları](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Yinelemeli veritabanı geliştirme gerçekleştiriliyor:** Geliştiriciler projenin parçalarını kullanıma alabilir ve bunları yalıtılmış bir geliştirme ortamında güncelleştirebilir. Bu ortam türünü kullanarak, ekibinizin diğer üyelerini etkilemeden değişikliklerinizi test edebilirsiniz. Değişiklikler tamamlandıktan sonra, diğer ekip üyelerinin değişiklikleri alabileceği ve bunları bir test sunucusuna dağıtabeceği sürüm denetimine geri döndüğünüzde dosyaları kontrol edersiniz. | - [Project odaklı çevrimdışı veritabanı geliştirme (SQL Server Veri Araçları)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Transact-SQL hata ayıklayıcı (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Prototip oluşturma, test sonuçlarını doğrulama ve veritabanı komut dosyalarını ve nesnelerini değiştirme:** bu ortak görevlerden herhangi birini gerçekleştirmek için Transact-SQL düzenleyicisini kullanabilirsiniz. | - [Sorgu ve metin düzenleyicileri (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
