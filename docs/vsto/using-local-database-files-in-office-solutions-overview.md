---
title: Office çözümlerinde yerel veritabanı dosyalarını kullanma genel bakış
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ea260a6286c8a923d56ab7a5088b55de57004489
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62982246"
---
# <a name="use-local-database-files-in-office-solutions-overview"></a>Office çözümlerinde yerel veritabanı dosyalarını kullanma genel bakış
  Office çözümünüzde SQL Server Express (*. mdf*) dosyası veya Microsoft Office erişim (*. mdb*) dosyası gibi bir veritabanı dosyası ekleyebilirsiniz. Bu, son kullanıcıların, örneğin tek bir bilgisayarda kullanılan yerel bir envanter çözümünde, merkezi bir veritabanının saklanması gerekmediği durumlarda yerel bir veritabanını korumalarını sağlar.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="import-the-database-file-into-a-project"></a>Veritabanı dosyasını bir projeye içeri aktarma
 Veritabanı dosyasını projenize aktarmak için, veritabanı dosyasını temel alan bir veri kaynağı oluşturmak üzere **veri kaynağı Yapılandırma Sihirbazı** ' nı kullanın. Sihirbaz, veritabanı dosyasını ve yazılmış bir veri kümesini projenize ekler.

## <a name="deploy-the-database-file"></a>Veritabanı dosyasını dağıtma
 **Veri kaynağı Yapılandırma Sihirbazı** , yerel veritabanı dosyasına bağlantı oluşturmak için göreli bir yol kullanır. Bu, dosyaların göreli konumlarını koruyabilmeniz durumunda çözümü bir bilgisayardan diğerine kopyalamanızı sağlar.

 Çözümünüzü bir sunucuya dağıtır ve ardından belgeyi her bir son kullanıcıya dağıtırsanız, veritabanı dosyasını da el ile dağıtmanız ve belgeye göre aynı konuma kurmanız gerekir. Bu, veritabanı dosyasını da taşımadığı takdirde son kullanıcının belgeyi veya bilgisayarındaki yeni bir konuma taşıyamayacağı anlamına gelir.

## <a name="local-database-files-and-caching-the-dataset"></a>Yerel veritabanı dosyaları ve veri kümesini önbelleğe alma
 Excel ve Microsoft Office Word 'Ün Microsoft Office belge düzeyi çözümlerinde, DataSet örneğini özniteliğiyle işaretleyerek belgedeki veri kümelerini önbelleğe alabilirsiniz <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> . **Veri kaynağı Yapılandırma Sihirbazı**'nı kullanarak veritabanı dosyasını projenize eklediğinizde, bir türü belirtilmiş veri kümesi projenize otomatik olarak eklenir. <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>Veriler kullanıcının bilgisayarında zaten yerel olduğundan, bu veri kümesine uygulanması nadiren gereklidir. Daha fazla bilgi için bkz. [önbelleği verileri](../vsto/caching-data.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Önbellek verileri](../vsto/caching-data.md)
