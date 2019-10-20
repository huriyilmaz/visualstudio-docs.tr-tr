---
title: Veritabanı projeleri ve DAC projeleri
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 11e60c43e2b9935f4aaf2ffcc5d5c7e3683665d1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648585"
---
# <a name="database-projects-and-data-tier-applications"></a>Veritabanı projeleri ve veri katmanı uygulamaları

Veritabanı projelerini kullanarak yeni veritabanları, yeni veri katmanı uygulamaları (PACS) oluşturabilir ve mevcut veritabanlarını ve veri katmanı uygulamalarını güncelleştirebilirsiniz. Hem veritabanı projeleri hem de DAC projeleri, bu teknikleri yönetilen veya yerel koda uyguladığınız şekilde veritabanı geliştirme çabalarınıza sürüm denetimi ve proje yönetimi teknikleri uygulamanızı sağlar. Bir DAC projesi, veritabanı projesi veya sunucu projesi oluşturarak ve sürüm denetimi altına koyarak, geliştirme takımınızın veritabanlarına ve veritabanı sunucularına yapılan değişiklikleri yönetmesine yardımcı olabilirsiniz. Ekibinizin üyeleri, takım ile paylaşmadan önce, yalıtılmış bir geliştirme ortamında veya korumalı alanda değişiklik yapmak, derlemek ve test etmek için dosyaları kullanıma alabilir. Kod kalitesinin sağlanmasına yardımcı olmak için ekibiniz, değişiklikleri üretime dağıtmadan önce hazırlama ortamında veritabanının belirli bir sürümüne yönelik tüm değişiklikleri bitirebilmeniz ve test edebilir.

Veri katmanı uygulamaları tarafından desteklenen veritabanı özelliklerinin bir listesi için bkz. [SQL Server nesneleri Için dac desteği](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions). Veritabanınızda veri katmanı uygulamaları tarafından desteklenmeyen özellikler kullanıyorsanız, veritabanınızdaki değişiklikleri yönetmek için bir veritabanı projesi kullanmanız gerekir.

## <a name="common-high-level-tasks"></a>Ortak üst düzey görevler

| Üst düzey görev | Destekleyici İçerik |
| - | - |
| **Veri katmanı uygulamasının geliştirilmesini başlatın:** Veri katmanı uygulaması (DAC) kavramı SQL Server 2008 ile tanıtılmıştı. DAC bir SQL Server veritabanının tanımını ve bir istemci-sunucu veya 3 katmanlı uygulama tarafından kullanılan destekleyici örnek nesnelerini içerir. DAC, tablolar ve görünümler gibi veritabanı nesnelerini, örneğin oturum açma işlemleri gibi örnek varlıklarla birlikte içerir. Visual Studio 'Yu kullanarak bir DAC projesi oluşturabilir, bir DAC paket dosyası oluşturabilir ve DAC paket dosyasını SQL Server veritabanı altyapısının bir örneğine dağıtım için bir veritabanı yöneticisine gönderebilirsiniz. | [veri katmanı uygulamalarını](/sql/relational-databases/data-tier-applications/data-tier-applications) - <br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Yinelemeli veritabanı geliştirme gerçekleştiriliyor:** Geliştiriciler projenin parçalarını kullanıma alabilir ve bunları yalıtılmış bir geliştirme ortamında güncelleştirebilir. Bu ortam türünü kullanarak, ekibinizin diğer üyelerini etkilemeden değişikliklerinizi test edebilirsiniz. Değişiklikler tamamlandıktan sonra, diğer ekip üyelerinin değişiklikleri alabileceği ve bunları bir test sunucusuna dağıtabeceği sürüm denetimine geri döndüğünüzde dosyaları kontrol edersiniz. | - [projeye dayalı çevrimdışı veritabanı geliştirme (SQL Server veri araçları)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Transact-SQL Debugger (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Prototip oluşturma, test sonuçlarını doğrulama ve veritabanı komut dosyalarını ve nesnelerini değiştirme:** Bu ortak görevlerden herhangi birini gerçekleştirmek için Transact-SQL düzenleyicisini kullanabilirsiniz. | [sorgu ve metin düzenleyicileri -  (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)