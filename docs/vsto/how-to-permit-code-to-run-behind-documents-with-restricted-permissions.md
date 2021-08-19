---
title: Kodun, kısıtlı izinlerle belgelerin arkasında çalışmasına izin verme
description: Visual Studio Office geliştirme araçlarını kullanarak kodun kısıtlanmış izinlerle birlikte çalıştırılmasına nasıl izin verileceğini öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 366c8716995f0f5e88707d738957fc4ec0476a50
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083394"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Nasıl yapılır: kodun, kısıtlı izinlerle belgelerin arkasında çalışmasına Izin verme
  bir belge veya çalışma kitabıyla izinleri kısıtlamak için Microsoft Office bilgi Rights Management (ırm) özelliğini kullanabilirsiniz. varsayılan olarak, kısıtlanmış Microsoft Office Word belgesi veya Microsoft Office Excel çalışma kitabının arkasındaki kodun çalışmasına izin verilmez. Varsayılan değer olarak, yönetilen kod uzantılarınızın nesne modeline erişebilmesi ve çözümünüzün çalışması için değiştirebilirsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 İzin ayarlarını değiştirebilmek için belge veya çalışma kitabının yazarı veya tam denetim erişiminin olması gerekir.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Kodun, kısıtlı izinlerle belgelerin arkasında çalışmasına izin vermek için

1. Belge veya çalışma kitabını Word veya Excel açın.

2. **Dosya** sekmesine tıklayın, **hazırla** seçeneğinin üzerine gelin, **izin kısıtla**' nın üzerine gelin ve ardından **kısıtlı erişim**' e tıklayın.

   > [!NOTE]
   > ilk kullanımda, Windows Rights Management istemcisini yüklemeniz istenir. İstemcisini yükledikten sonra, adımları tekrarlamanız gerekebilir.

3. **İzin** iletişim kutusunda **Bu belge için izinleri kısıtla**' yı seçin ve **daha sonra diğer seçenekler**' e tıklayın.

4. **Kullanıcılar Için ek izinler** altında, **içeriğe programlamayla erişim**' i seçin.

   sözcük veya Excel, nesne modeline programlı erişime izin verir.

## <a name="see-also"></a>Ayrıca bkz.
- [Bilgi hakları yönetimine ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Belge düzeyi çözümlerde Belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Office belgelerde parola koruması](../vsto/password-protection-on-office-documents.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office çözümleri güvenli hale getirme](../vsto/securing-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
