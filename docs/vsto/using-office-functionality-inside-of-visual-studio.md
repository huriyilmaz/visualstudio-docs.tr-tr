---
title: Uygulamanın Office işlevlerini Visual Studio
description: Belge düzeyindeki bir projeden belge ve ilişkili uygulamanın doğrudan belgeyle çalışabilirsiniz Visual Studio içinde nasıl barındırıldıklarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 1e08f5a0189b50ee37c240ad32556e4efd7d3fa00c759f37e54cf5d9e73de368
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121226056"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Uygulamanın Office işlevlerini Visual Studio
  Belge düzeyinde bir proje ekleyebilirsiniz. Belge ve ilişkili uygulama, belgeyi doğrudan Visual Studio ve çalışmanızı sağlar. Visual Studio'da Microsoft Office bir uygulama Visual Studio genellikle beklendiği gibi çalışır. Ancak, uygulamanın bazı işlevleri farklıdır veya erişilemez.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Belge koruması
 Microsoft Office Word ve Microsoft Office Excel, projeleriniz için kullanabileceğiniz belge koruma özellikleri sunar. Ancak belge açıkken belge koruması etkinse Visual Studio bazı tasarım değişiklikleri yapabilirsiniz. Daha fazla bilgi için [bkz. Belge düzeyi çözümlerde belge koruması.](../vsto/document-protection-in-document-level-solutions.md)

## <a name="information-rights-management"></a>Bilgi hakları yönetimi
 Bilgi Rights Management (IRM), Word ve Microsoft Office 'de Microsoft Office Excel. IRM, yetkisiz kişilerin hassas bilgileri görüntülemesini veya değiştirmesini önlemeye yardımcı olabilir. Ancak, IRM kodunuzun çalışmasını da önlenebilir. Daha fazla bilgi için [bkz. Bilgi hakları yönetimi ve yönetilen kod uzantılarına genel bakış.](../vsto/information-rights-management-and-managed-code-extensions-overview.md)

## <a name="password-protection"></a>Parola koruması
 Microsoft Office Word belgeleri Microsoft Office Excel çalışma kitapları, parolayı bilmiyor biri tarafından açılamay için kullanılabilir. Parola koruması Word ve Excel farklı şekilde ele Excel geliştirme sürecinizi etkileyebilir. Daha fazla bilgi için [bkz. Belgelerde Office.](../vsto/password-protection-on-office-documents.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Belge düzeyi çözümlerde belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Bilgi hakları yönetimi ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Office belgelerde parola koruması](../vsto/password-protection-on-office-documents.md)
- [Nasıl Office: Kod çalıştırmadan Office çözümleri açma](../vsto/how-to-open-office-solutions-without-running-code.md)
