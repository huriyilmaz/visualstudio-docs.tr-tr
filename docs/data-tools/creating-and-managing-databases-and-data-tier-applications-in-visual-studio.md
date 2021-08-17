---
title: Veritabanı projeleri ve DAC projeleri
description: Veritabanı projeleri ve veri katmanı uygulamaları (DAC) hakkında bilgi okuyun. Veritabanı projelerini kullanarak yeni veritabanları oluşturun, yeni DAC'ler oluşturun ve mevcut VERITABANLARı ile DAC'leri güncelleştirin.
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
ms.openlocfilehash: 0d9ed2d258fba0e8c6e1970bc758d0285bb4276c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122052830"
---
# <a name="database-projects-and-data-tier-applications"></a>Veritabanı projeleri ve veri katmanı uygulamaları

Veritabanı projelerini kullanarak yeni veritabanları, yeni veri katmanı uygulamaları (DAC) oluşturabilir ve mevcut veritabanlarını ve veri katmanı uygulamalarını güncelleştirebilirsiniz. Hem veritabanı projeleri hem de DAC projeleri, veritabanı geliştirme çalışmalarınıza sürüm denetimi ve proje yönetimi tekniklerini yönetilen veya yerel koda uygulamakla aynı şekilde uygulamanıza olanak sağlar. DAC projesi, veritabanı projesi veya sunucu projesi oluşturarak ve sürüm denetimi altına koyarak geliştirme takımınıza veritabanlarında ve veritabanı sunucularında yapılan değişiklikleri yönetmeye yardımcı olabilirsiniz. Takım üyeleri daha sonra yalıtılmış bir geliştirme ortamında veya korumalı alanda değişiklik yapmak, derlemek ve test etmek için dosyaları takımla paylaşmadan önce kontrol eder. Kodunun kalitesini sağlamaya yardımcı olmak için, değişiklikleri üretime dağıtmadan önce takımınız hazırlama ortamında veritabanının belirli bir sürümü için tüm değişiklikleri tamamlar ve test edebilir.

Veri katmanı uygulamaları tarafından desteklenen veritabanı özelliklerinin listesi için bkz. Nesne nesneleri için [DAC SQL Server desteği.](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions) Veritabanınız içinde veri katmanı uygulamaları tarafından desteklenen özellikler kullanıyorsanız, veritabanınıza yapılan değişiklikleri yönetmek için bunun yerine bir veritabanı projesi kullansanız iyi olur.

## <a name="common-high-level-tasks"></a>Genel üst düzey görevler

| High-Level Görevi | Destekleyici İçerik |
| - | - |
| **Veri katmanı uygulaması geliştirmeyi başlatma:** Veri katmanı uygulaması (DAC) kavramı 2008 yılında SQL Server ortaya çıktı. DAC, bir istemci-SQL Server veya 3 katmanlı uygulama tarafından kullanılan desteklenen örnek nesnelerinin tanımını içerir. DAC, oturum açma bilgileri gibi örnek varlıklarla birlikte tablolar ve görünümler gibi veritabanı nesnelerini içerir. Visual Studio projesini oluşturmak, DAC paket dosyası oluşturmak ve DAC paket dosyasını bir veritabanı yöneticisine gönderebilirsiniz. Bu dosya, SQL Server veritabanı altyapısının bir örneğine dağıtım için kullanılır. | - [Veri katmanı uygulamaları](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **Veritabanı geliştirmeyi iterative gerçekleştirme:** Geliştiriciler projenin bölümlerini kontrol eder ve yalıtılmış bir geliştirme ortamında güncelleştirer. Bu tür bir ortamı kullanarak değişikliklerinizi ekibin diğer üyelerini etkilemeden test yapabilirsiniz. Değişiklikler tamamlandıktan sonra dosyaları sürüm denetimine geri gönderirsiniz; burada diğer ekip üyeleri değişikliklerinizi ediner ve bunları bir test sunucusuna hazırlar ve dağıtır. | - [Project odaklı çevrimdışı veritabanı geliştirme (SQL Server Veri Araçları)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Transact-SQL hata ayıklayıcısı (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **Örnek oluşturma, test sonuçlarını doğrulama ve veritabanı betikleri ile nesnelerini değiştirme:** Transact-SQL düzenleyicisini kullanarak bu ortak görevlerden herhangi birini gerçekleştirebilirsiniz. | - [Sorgu ve metin düzenleyicileri (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
