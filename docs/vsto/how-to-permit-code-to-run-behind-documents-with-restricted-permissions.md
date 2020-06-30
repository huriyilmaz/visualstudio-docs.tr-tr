---
title: Kodun, kısıtlı izinlerle belgelerin arkasında çalışmasına izin verme
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 15cfb7ebf2f4f71e892820206f0dd1d006639992
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547517"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Nasıl yapılır: kodun, kısıtlı izinlerle belgelerin arkasında çalışmasına Izin verme
  Bir belge veya çalışma kitabıyla izinleri kısıtlamak için Microsoft Office bilgi Rights Management (ıRM) özelliğini kullanabilirsiniz. Varsayılan olarak, kısıtlı bir Microsoft Office Word belgesi veya Microsoft Office Excel çalışma kitabının arkasındaki kodun çalışmasına izin verilmez. Varsayılan değer olarak, yönetilen kod uzantılarınızın nesne modeline erişebilmesi ve çözümünüzün çalışması için değiştirebilirsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 İzin ayarlarını değiştirebilmek için belge veya çalışma kitabının yazarı veya tam denetim erişiminin olması gerekir.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Kodun, kısıtlı izinlerle belgelerin arkasında çalışmasına izin vermek için

1. Belgeyi veya çalışma kitabını Word veya Excel 'de açın.

2. **Dosya** sekmesine tıklayın, **hazırla**seçeneğinin üzerine gelin, **izin kısıtla**' nın üzerine gelin ve ardından **kısıtlı erişim**' e tıklayın.

   > [!NOTE]
   > İlk kez kullandığınızda, Windows Rights Management istemcisini yüklemeniz istenir. İstemcisini yükledikten sonra, adımları tekrarlamanız gerekebilir.

3. **İzin** iletişim kutusunda **Bu belge için izinleri kısıtla**' yı seçin ve **daha sonra diğer seçenekler**' e tıklayın.

4. **Kullanıcılar Için ek izinler**altında, **içeriğe programlamayla erişim**' i seçin.

   Word veya Excel, nesne modeline programlı erişime izin verir.

## <a name="see-also"></a>Ayrıca bkz.
- [Bilgi hakları yönetimine ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Belge düzeyi çözümlerde Belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Office belgelerinde parola koruması](../vsto/password-protection-on-office-documents.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
