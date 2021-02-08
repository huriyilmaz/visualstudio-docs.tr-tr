---
title: Visual Studio içinde Office işlevselliğini kullanma
description: Belge düzeyi bir projeden belge ve ilişkili uygulamanın Visual Studio içinde nasıl barındırıldığı hakkında bilgi edinmek için doğrudan belgeyle birlikte çalışabilirsiniz.
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
ms.workload:
- office
ms.openlocfilehash: 258ea4529a558c91eb115b82b35def4ca4ab6561
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838249"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Visual Studio içinde Office işlevselliğini kullanma
  Belge düzeyinde bir proje oluşturduğunuzda, belge ve ilişkili uygulama Visual Studio içinde barındırılır, böylece doğrudan belgeyle tasarlayabilir ve çalışabilirsiniz. Visual Studio 'da açık bir Microsoft Office uygulamanız varsa, genellikle beklendiği gibi çalışmaktadır. Ancak, bazı uygulama işlevleri farklı veya erişilemez olur.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Belge koruması
 Word ve Microsoft Office Excel Microsoft Office, projelerinizde kullanabileceğiniz belge koruma özellikleri sunar. Öte yandan belge, Visual Studio 'da açıkken belge koruma etkinleştirilmişse, bazı tasarım değişiklikleri yapmasını engelleyebilir. Daha fazla bilgi için bkz. [belge düzeyi çözümlerinde belge koruması](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Bilgi Hakları Yönetimi
 Bilgi Rights Management (ıRM) Microsoft Office Word ve Excel Microsoft Office bulunabilir. IRM, yetkisiz kişilerin hassas bilgileri görüntülemesini veya değiştirmesini önlemeye yardımcı olabilir. Bununla birlikte, ıRM de kodunuzun çalışmasını engelleyebilir. Daha fazla bilgi için bkz. [bilgi hakları yönetimi ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Parola koruması
 Microsoft Office Word belgeleri ve Microsoft Office Excel çalışma kitapları, parolayı kullanmayan birisi tarafından açılabilmeleri için ayarlanabilir. Parola koruması Word ve Excel 'de farklı şekilde işlenir ve geliştirme sürecinizi etkileyebilir. Daha fazla bilgi için bkz. [Office belgelerinde parola koruması](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Belge düzeyi çözümlerde Belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Bilgi hakları yönetimine ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Office belgelerinde parola koruması](../vsto/password-protection-on-office-documents.md)
- [Nasıl yapılır: kod çalıştırmadan Office çözümlerini açma](../vsto/how-to-open-office-solutions-without-running-code.md)
