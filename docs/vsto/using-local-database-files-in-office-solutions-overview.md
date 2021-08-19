---
title: Çözümlerde yerel veritabanı dosyalarını Office genel bakış
description: Office çözümünüzde SQL Server Express (.mdf) dosyası veya Microsoft Office Access (.mdb) dosyası gibi bir veritabanı dosyasını nasıl dahil Office öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], data
- data [Office development in Visual Studio], local
- local data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f2e7dc3346ccb2104e5350968d2f983b1c2e1c69
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099431"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Çözümlerde yerel veritabanı dosyalarını Office genel bakış
  SQL Server Express (*.mdf*) dosyası veya Microsoft Office Access (*.mdb*) dosyası gibi bir veritabanı dosyasını Office kullanabilirsiniz. Bu, merkezi bir veritabanının bakımının gerekli olduğu durumlarda (örneğin, yalnızca tek bir bilgisayarda kullanılan yerel bir envanter çözümünde) son kullanıcıların yerel bir veritabanını sürdürmesini sağlar.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Veritabanı dosyasını projeye aktarma
 Veritabanı dosyasını projenize içeri aktarın, veritabanı **dosyasını** temel alan bir veri kaynağı oluşturmak için Veri Kaynağı Yapılandırma Sihirbazı'nı kullanın. Sihirbaz, veritabanı dosyasını ve türü belirtilen veri kümelerini projenize ekler.

## <a name="deploy-the-database-file"></a>Veritabanı dosyasını dağıtma
 Veri **Kaynağı Yapılandırma Sihirbazı,** yerel veritabanı dosyasına bağlantılar oluşturmak için göreli bir yol kullanır. Bu, dosyaların göreli konumlarını sürdürürsanız çözümü bir bilgisayardan diğerine kopyalamaya olanak sağlar.

 Çözümlerinizi bir sunucuya dağıtır ve belgeyi her son kullanıcıya dağıtırsanız, veritabanı dosyasını el ile dağıtmanız ve belgeyle aynı konumda yüklemeniz gerekir. Bu, son kullanıcının, veritabanı dosyasını taşımadıkça belgeyi kendi bilgisayarına yeni bir konuma taşıması anlamına gelir.

## <a name="local-database-files-and-caching-the-dataset"></a>Yerel veritabanı dosyaları ve veri kümesi önbelleğe alma
 Microsoft Office Excel ve Microsoft Office Word için belge düzeyi çözümlerde, veri kümesi örneğini özniteliğiyle işaretleyerek belgede veri kümelerini önbelleğe <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> alın. Veri Kaynağı Yapılandırma Sihirbazı'nı kullanarak veritabanı dosyasını projenize eklerken, projenize otomatik olarak türü eklenmiş bir veri kümesi eklenir. Veriler kullanıcının bilgisayarına zaten yerel olduğundan, bu <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> veri kümesine uygulamak nadiren gereklidir. Daha fazla bilgi için [bkz. Verileri önbelleğe alın.](../vsto/caching-data.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Nasıl kullanılır: Belgeleri bir veritabanındaki verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl kullanılır: Bir veri kaynağını konak denetiminden verilerle güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
- [Önbellek verileri](../vsto/caching-data.md)
