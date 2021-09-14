---
title: Kodun kısıtlı izinlerle docs'un arkasında çalışmasına izin ver
description: Uygulama geliştirme araçlarını kullanarak belgelerin arkasında kısıtlı izinlerle kod çalıştırmaya izin Office nasıl izin ver Visual Studio.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634033"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Nasıl kullanılır: Kodun kısıtlı izinlerle belgelerin arkasında çalışmasına izin verme
  Bir belge veya çalışma kitabına Rights Management kısıtlamak için Microsoft Office'nin Information Rights Management (IRM) özelliğini kullanabilirsiniz. Varsayılan olarak, kısıtlanmış bir Word Microsoft Office veya Microsoft Office Excel çalışma kitabının arkasındaki kodun çalışmasına izin verilmez. Yönetilen kod uzantılarınız nesne modeline erişemeyecek ve çözümünüz çalışacak şekilde varsayılanı değiştirebilirsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 İzin ayarlarını değiştiremeniz için belgenin veya çalışma kitabının yazarı veya Tam Denetim erişiminizin olması gerekir.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Kodun kısıtlı izinlerle belgelerin arkasında çalışmasına izin verme

1. Belgeyi veya çalışma kitabını Word'de veya Excel.

2. Dosya **sekmesine tıklayın,** Hazırla'nın **üzerine gelin,** İzni **Kısıtla'nın üzerine gelin** ve ardından Kısıtlı **Erişim'e tıklayın.**

   > [!NOTE]
   > İlk kullanımda, Windows Rights Management istemcisini yüklemeniz istenir. İstemciyi yükledikten sonra adımları yinelemeniz gerekir.

3. İzin iletişim **kutusunda Bu** belge için izni **kısıtla'yı seçin** ve ardından Diğer Seçenekler'e **tıklayın.**

4. Kullanıcılar **için ek izinler altında,** **içeriğe program aracılığıyla eriş'i seçin.**

   Word Excel nesne modeline programlı erişime izin veecek.

## <a name="see-also"></a>Ayrıca bkz.
- [Bilgi hakları yönetimi ve yönetilen kod uzantılarına genel bakış](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Belge düzeyi çözümlerde belge koruması](../vsto/document-protection-in-document-level-solutions.md)
- [Office belgelerde parola koruması](../vsto/password-protection-on-office-documents.md)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
