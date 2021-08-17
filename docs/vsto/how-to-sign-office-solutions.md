---
title: 'Nasıl Office: Office imzalama'
description: Bir sertifikayı kanıt olarak kullanarak Microsoft Office çözümünüze nasıl güven verycenizi öğrenin.
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
ms.openlocfilehash: 914a23df8b1a1cff3f07c2476fa4c55e44d17847021d955978ed9a9e73d04735
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394205"
---
# <a name="how-to-sign-office-solutions"></a>Nasıl Office: Office imzalama
  Bir çözümü imzalarsanız, sertifikayı kanıt olarak kullanarak çözüme güven vesersiniz. Birden çok çözüm için aynı sertifikayı kullanabilirsiniz ve tüm çözümlere ek güvenlik ilkesi güncelleştirmesi gerekmayacak şekilde güvenilir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 uygulama ve dağıtım bildirimlerini Bildirim Oluşturma ve Düzenleme Aracı (*mage.exe* ve *mageui.exe)* kullanarak el ile düzenlersanız, bunları kullanamadan önce bildirimleri yeniden imzalamanız gerekir. Daha fazla bilgi için, [bkz. How to: Re-sign application and deployment manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

## <a name="sign-by-using-a-certificate"></a>Sertifika kullanarak imzalama
 Sertifika, benzersiz bir anahtar ve çözüm yayımcısı kimliğini içeren bir dosyadır. Bir sertifika yetkilisini kullanarak sertifika satın almak veya kendi sertifikanızı oluşturmak ve sertifika yetkilisi imzalamak için kullanabilirsiniz.

 Visual Studio ayıklamayı Office için geçici bir sertifika ile çözüm imzalar. Dağıtılan çözümlerde geçici sertifikayı kanıt olarak kullanmamanız gerekir.

### <a name="to-sign-an-office-solution-by-using-a-certificate"></a>Sertifika kullanarak Office çözümü imzalamak için

1. Yeni **Project** _SolutionName Özellikleri'ne_**tıklayın.**

2. İmzalama **sekmesine** tıklayın.

3. Bildirimlerini **imzala'ClickOnce seçin.**

4. Depodan Seç veya **Dosyadan** **Seç'e tıklar** ve sertifikaya giderek sertifikayı bulun.

5. Doğru sertifikanın çalıştığını doğrulamak için Diğer **Ayrıntılar'a tıklar** ve sertifika bilgilerini görüntüebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Çözüme güven Office ver](../vsto/granting-trust-to-office-solutions.md)
- [İmzalama Sayfası, Proje Tasarımcısı](../ide/reference/signing-page-project-designer.md)
