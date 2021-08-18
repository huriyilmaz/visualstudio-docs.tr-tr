---
title: Visual Studio içinde Office işlevselliği kullanın
description: belge düzeyindeki bir projeden belge ve ilişkili uygulamanın Visual Studio içinde nasıl barındırıldığı hakkında bilgi edinin, böylece doğrudan belgeyle çalışabilirsiniz.
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
ms.openlocfilehash: ee597766c9444b837ff0abe29146b0373264906e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046236"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Visual Studio içinde Office işlevselliği kullanın
  belge düzeyinde bir proje oluşturduğunuzda, belge ve ilişkili uygulama Visual Studio içinde barındırılır, böylece doğrudan belgeyle tasarlayabilir ve çalışabilirsiniz. Visual Studio açık bir Microsoft Office uygulamanız varsa, genellikle beklendiği gibi çalışmaktadır. Ancak, bazı uygulama işlevleri farklı veya erişilemez olur.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Belge koruması
 Microsoft Office Word ve Microsoft Office Excel, projelerinizde kullanabileceğiniz belge koruma özellikleri sunar. ancak, belge Visual Studio açıkken belge koruması etkinse, bazı tasarım değişiklikleri yapmasını engelleyebilir. Daha fazla bilgi için bkz. [belge düzeyi çözümlerinde belge koruması](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Bilgi Hakları Yönetimi
 bilgi Rights Management (ırm) Microsoft Office Word ve Microsoft Office Excel kullanılabilir. IRM, yetkisiz kişilerin hassas bilgileri görüntülemesini veya değiştirmesini önlemeye yardımcı olabilir. Bununla birlikte, ıRM de kodunuzun çalışmasını engelleyebilir. Daha fazla bilgi için bkz. [bilgi hakları yönetimi ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Parola koruması
 Microsoft Office Word belgeleri ve Microsoft Office Excel çalışma kitapları, parolayı kullanmayan birisi tarafından açılabilmeleri için ayarlanabilir. parola koruması Word ve Excel içinde farklı işlenir ve geliştirme sürecinizi etkileyebilir. daha fazla bilgi için bkz. [Office belgelerdeki parola koruması](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Belge düzeyi çözümlerde Belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Bilgi hakları yönetimine ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Office belgelerde parola koruması](../vsto/password-protection-on-office-documents.md)
- [nasıl yapılır: kod çalıştırmadan Office çözümlerini açma](../vsto/how-to-open-office-solutions-without-running-code.md)
