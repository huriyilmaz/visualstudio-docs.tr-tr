---
title: Belge düzeyi çözümlerde belge koruması
description: Belge düzeyindeki projelerde Word'Microsoft Office ve Microsoft Office Excel özelliklerini nasıl kullanabileceğiniz hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio], restricted permissions
- documents [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cc11241057a32d24746eb9eabbc6a7b6526c9eaa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026479"
---
# <a name="document-protection-in-document-level-solutions"></a>Belge düzeyi çözümlerde belge koruması
  Belge düzeyi projelerde Word'Microsoft Office ve Microsoft Office Excel koruma özelliklerini kullanabilirsiniz. Bu özellikler, yetkisiz kullanıcıların belgenin korumalı kısımlarında değişiklik yapmalarını engelleyebilir.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Bu Excel kullanarak, çalışma kitabı tasarımcıda açıkken korumayı açıp kapatabilirsiniz. Word'i kullanarak korumayı yalnızca tasarımcının dışında açsanız iyi olabilir. Çalışma zamanında, hem Word hem de Excel için korumayı program aracılığıyla etkinleştirin veya devre dışı Excel.

 Tasarımcıda açık olan bir belgede belge koruması etkinleştirildiğinde, tüm  denetimler Araç Kutusundan kaldırılır veya kullanılamaz  duruma gelir ve Veri Kaynakları penceresinden belgeye hiçbir şeyi sürükleyesiniz.

## <a name="serverdocument-and-protected-documents"></a>ServerDocument ve korumalı belgeler
 Bir belge korunuyorsa, veri önbelleğine belgenin dışından erişilemez. Korumalı bir belgede önbelleğe alınan verileri almak veya işlemek için sınıfını veya <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfın diğer yöntemlerini <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> kullanamazsınız.

## <a name="word-document-protection-in-the-designer"></a>Tasarımcıda Word belge koruması
 Word belge veya şablonu açıkken bir Word belgesine veya şablonuna koruma Visual Studio, tasarımcıda korumayı zorlamaya başamazsınız. Belge tasarım modundayken açıkken Visual Studio ve korumayı zorlamaya başlamadan önce çalışma modunda olması gerekir.

 Ancak, koruma etkinleştirilmiş mevcut bir Word belgesini kullanan bir proje ekleyebilirsiniz, belge tasarımcıda açıkken korunur. Belgenin korumalı bölümlerini düzenleyemezsiniz, ancak yine de belgeyi otomatikleştirmek için Kod Düzenleyicisi'nde kod yazabilirsiniz. Belge açıkken koruma etkinse projeyi de Visual Studio.

 Belge tasarımcıda açıkken korumayı kapatabilirsiniz; böylece belgeyi düzenleyebilir ve projeyi ekleyebilirsiniz. Hata ayıklarken tasarımcıda kopya için korumayı kapatamaz; hata ayıklama sırasında açılan belge, tasarımcıda açık olandan ayrı bir kopyadır (çıkış kopyası Visual Basic için *\bin* dizininde ve C# için *\bin\debug* dizininde depolanır).

 Projeyi Visual Studio'da kapatarak, proje dizininde yer alan belgenin kopyasını açarak ve korumayı açarak tasarımcıda açılan belgenin kopyasında korumayı etkinleştirebilirsiniz.

## <a name="enforce-word-document-protection-on-build"></a>Derlemede Word belge korumasını zorlama
 Visual Studio belge hata ayıklama için açıldığında korumanın etkinleştirilmesi için derleme işlemi sırasında Word belgeleri ve şablonları için korumayı zorlamaya başlar. Belge boş bir parolayla korunur.

 Derleme sırasında koruma etkinleştirildiğinden, belge olayında özel durumlara neden olan veya uygulamanın davranışını değiştiren bir kod varsa, bu kod doğru <xref:Microsoft.Office.Tools.Word.Document.Startup> şekilde hata ayıklanabilecektir. Belge açıldıktan sonra korumayı etkinleştirirsiniz, başlatma kodunda hata ayıklama veya test kullanılamaz.

## <a name="setting-the-password"></a>Parolayı ayarlama
 Visual Studio korumayı otomatik olarak sağlar, ancak varsayılan olarak parola sağlar. Belge korumasının bir parolası olması için çözüm dağıtmadan önce bunu eklemeniz gerekir. Parola eklemek, yetkili kullanıcıların belgeden korumayı kaldırmasına olanak sağlar; parola olmadan koruma kolayca kaldırılamaz. Parola ayarlama hakkında ayrıntılı bilgi için belirli bir uygulamanın Office bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Belgeleri ve belgelerin parçalarını program aracılığıyla koruma](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Office örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Bilgi hakları yönetimi ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Office belgelerde parola koruması](../vsto/password-protection-on-office-documents.md)
- [Nasıl kullanılır: Kodun kısıtlı izinlerle belgelerin arkasında çalışmasına izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
