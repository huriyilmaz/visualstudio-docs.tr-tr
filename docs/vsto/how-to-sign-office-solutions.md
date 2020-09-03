---
title: 'Nasıl yapılır: Office çözümlerini Imzalama'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 23afc171fd97620b3e6801b8d199da6890198d8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545762"
---
# <a name="how-to-sign-office-solutions"></a>Nasıl yapılır: Office çözümlerini Imzalama
  Bir çözümü imzalayıp, kanıt olarak sertifikayı kullanarak çözüme güven verebilirsiniz. Aynı sertifikayı birden çok çözüm için kullanabilirsiniz ve tüm çözümlere ek güvenlik ilkesi güncelleştirmeleri olmadan güvenilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Uygulama ve dağıtım bildirimlerini Bildirim Oluşturma ve Düzenleme Aracı (*mage.exe* ve *mageui.exe*) kullanarak el ile düzenlerseniz, bunları kullanabilmeniz için önce bildirimleri yeniden imzalamanız gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: uygulama ve dağıtım bildirimlerini yeniden imzalama](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Sertifika kullanarak imzala
 Sertifika, bir benzersiz anahtar ve Çözüm yayımcısının kimliğini içeren bir dosyadır. Bir sertifika yetkilisinden sertifika satın alabilir veya kendi sertifikanızı oluşturabilir ve bir sertifika yetkilisi oturum açmasını sağlayabilirsiniz.

 Visual Studio, hata ayıklamayı etkinleştirmek için Office çözümlerini geçici bir sertifikayla imzalar. Dağıtılmış çözümlerinde geçici sertifikayı kanıt olarak kullanmamalısınız.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Bir Office çözümünü sertifika kullanarak imzalamak için

1. **Proje** menüsünde, _SolutionName_**özellikleri**' ne tıklayın.

2. **İmzalama** sekmesine tıklayın.

3. **ClickOnce bildirimlerini imzala**' yı seçin.

4. **Mağazadan Seç** ' e tıklayarak sertifikayı bulun veya dosyadan **seçim** yapın ve sertifikaya gidin.

5. Doğru sertifikanın kullanıldığını doğrulamak için, sertifika bilgilerini görüntülemek üzere **diğer ayrıntılar** ' a tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Office çözümlerine güven verme](../vsto/granting-trust-to-office-solutions.md)
- [İmzalama Sayfası, Proje Tasarımcısı](../ide/reference/signing-page-project-designer.md)
