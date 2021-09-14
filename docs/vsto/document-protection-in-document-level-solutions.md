---
title: Belge düzeyi çözümlerde Belge koruması
description: belge düzeyi projelerinde Microsoft Office Word ve Microsoft Office Excel koruma özelliklerini nasıl kullanabileceğinizi öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634118"
---
# <a name="document-protection-in-document-level-solutions"></a>Belge düzeyi çözümlerde Belge koruması
  belge düzeyi projelerinde Microsoft Office Word ve Microsoft Office Excel koruma özelliklerini kullanabilirsiniz. Bu özellikler yetkisiz kullanıcıların bir belgenin korunan bölümlerinde değişiklik yapmasını engeller.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Excel kullanarak, çalışma kitabı tasarımcıda açıkken korumayı etkinleştirebilir ve devre dışı bırakabilirsiniz. Word kullanarak korumayı yalnızca Tasarımcı dışında etkinleştirebilirsiniz. Çalışma zamanında, hem Word hem de Excel için korumayı programlı bir şekilde etkinleştirebilir veya devre dışı bırakabilirsiniz.

 Tasarımcıda açık olan bir belge üzerinde belge koruması etkinleştirildiğinde, tüm denetimler **araç kutusundan** kaldırılır veya kullanılamaz hale getirilir ve **veri kaynakları** penceresinden belgeye hiçbir şey sürükleyemezsiniz.

## <a name="serverdocument-and-protected-documents"></a>ServerDocument ve korumalı belgeler
 Bir belge korunuyorsa, veri önbelleğine belge dışından erişilemez. <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Korumalı bir belgede önbelleğe alınmış verileri almak veya işlemek ya da sınıfının diğer yöntemlerini kullanmak için sınıfını kullanamazsınız <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> .

## <a name="word-document-protection-in-the-designer"></a>Tasarımcıda Word belge koruması
 bir Word belgesi veya şablonuna Visual Studio açıkken koruma eklerseniz, tasarımcıda korumayı zorunlu hale başlatamazsınız. belge tasarım modunda, Visual Studio açıkken, korumayı zorlamaya başlayabilmeniz için önce çalışma modunda olmalıdır.

 Ancak, koruması etkin olan mevcut bir Word belgesini kullanan bir proje oluşturursanız, belge tasarımcıda açıldığında korunur. Belgenin korunan bölümlerini düzenleyemezsiniz, ancak belgeyi otomatik hale getirmek için kod düzenleyicisinde kod yazmaya devam edebilirsiniz. Ayrıca, belge Visual Studio açıkken koruma etkinleştirildiyse projeyi derlenemez.

 Belgeyi düzenlemek ve projeyi derlemek için belge tasarımcıda açıkken korumayı devre dışı bırakabilirsiniz. Hata ayıklarken tasarımcıda kopyalamaya yönelik korumayı devre dışı bırakabilirsiniz; hata ayıklama sırasında açılan belge, tasarımcıda açık olan ayrı bir kopyadır (çıktı kopyası Visual Basic için *\bin* dizininde ve C# için *\bin\debug* dizininde depolanır).

 Visual Studio içinde projeyi kapatarak, proje dizininde bulunan belgenin kopyasını açarak ve korumayı etkinleştirerek, tasarımcıda açılan belgenin kopyasında korumayı etkinleştirebilirsiniz ().

## <a name="enforce-word-document-protection-on-build"></a>Derlemede Word belge korumasını zorla
 Visual Studio, derleme işlemi sırasında Word belgelerinin ve şablonlarının korunmasını zorlamaya başlar, bu sayede belge hata ayıklama için açıldığında koruma etkinleştirilir. Belge boş bir parolayla korunuyor.

 <xref:Microsoft.Office.Tools.Word.Document.Startup>Uygulama, özel durumlara neden olabilecek veya uygulamanın davranışını değiştirebilen belge olayında kod varsa, bu kodun doğru şekilde ayıklanamayacağını belirten derleme sırasında koruma etkinleştirilir. Belge açıldıktan sonra korumayı etkinleştirirseniz, başlatma kodunun hataları ayıklanamaz veya test edilemez.

## <a name="setting-the-password"></a>Parolayı ayarlama
 Visual Studio otomatik olarak koruma sağlar, ancak varsayılan olarak parola sağlamaz. Belge korumasının bir parolası olmasını istiyorsanız çözümünüzü dağıtmadan önce eklemeniz gerekir. Parola eklemek yetkili kullanıcıların belgeden korumayı kaldırmasını sağlar; parola olmadan koruma kolayca kaldırılamaz. parola ayarlama hakkında daha fazla bilgi için bkz. belirli Office uygulamasındaki yardım.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: program aracılığıyla belgeleri ve belge parçalarını koruma](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md)
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)
- [Bilgi hakları yönetimine ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Office belgelerde parola koruması](../vsto/password-protection-on-office-documents.md)
- [Nasıl yapılır: kodun, kısıtlı izinlerle belgelerin arkasında çalışmasına Izin verme](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
