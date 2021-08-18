---
title: 'nasıl yapılır: Office çözümlerini imzalama'
description: kanıt olarak bir sertifika kullanarak Microsoft Office çözümünüze nasıl güven sağlayabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- certificates [Office development in Visual Studio], Office solutions
- security [Office development in Visual Studio], signing Office solutions
- signing manifests [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ab1fa5de20975b3c08d95906cef1288ebe8f4ec5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025978"
---
# <a name="how-to-sign-office-solutions"></a>nasıl yapılır: Office çözümlerini imzalama
  Bir çözümü imzalayıp, kanıt olarak sertifikayı kullanarak çözüme güven verebilirsiniz. Aynı sertifikayı birden çok çözüm için kullanabilirsiniz ve tüm çözümlere ek güvenlik ilkesi güncelleştirmeleri olmadan güvenilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 uygulama ve dağıtım bildirimlerini Bildirim Oluşturma ve Düzenleme Aracı (*mage.exe* ve *mageui.exe*) kullanarak el ile düzenlerseniz, bunları kullanabilmeniz için önce bildirimleri yeniden imzalamanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Sertifika kullanarak imzala
 Sertifika, bir benzersiz anahtar ve Çözüm yayımcısının kimliğini içeren bir dosyadır. Bir sertifika yetkilisinden sertifika satın alabilir veya kendi sertifikanızı oluşturabilir ve bir sertifika yetkilisi oturum açmasını sağlayabilirsiniz.

 hata ayıklamayı etkinleştirmek için geçici bir sertifikaya sahip çözümleri Office Visual Studio imzalar. Dağıtılmış çözümlerinde geçici sertifikayı kanıt olarak kullanmamalısınız.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>bir Office çözümünü sertifika kullanarak imzalamak için

1. **Project** menüsünde, _solutionname_**özellikleri**' ne tıklayın.

2. **İmzalama** sekmesine tıklayın.

3. **ClickOnce bildirimlerini imzala**' yı seçin.

4. **Mağazadan Seç** ' e tıklayarak sertifikayı bulun veya dosyadan **seçim** yapın ve sertifikaya gidin.

5. Doğru sertifikanın kullanıldığını doğrulamak için, sertifika bilgilerini görüntülemek üzere **diğer ayrıntılar** ' a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümleri güvenli hale getirme](../vsto/securing-office-solutions.md)
- [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md)
- [İmzalama Sayfası, Proje Tasarımcısı](../ide/reference/signing-page-project-designer.md)
