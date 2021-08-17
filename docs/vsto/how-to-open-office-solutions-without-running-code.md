---
title: 'Nasıl Office: Kod çalıştırmadan Office çözümleri açma'
description: Derleme kodunu çalıştırmadan yönetilen kod uzantıları içeren bir belgeyi veya çalışma kitabını açmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b7816072d0cb5ee55c753eea4e1d0bdf2e8bafe1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026245"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Nasıl Office: Kod çalıştırmadan Office çözümleri açma
  Son Microsoft Office uygulamanın Güvenlik ayarı Yüksek olarak ayarlansa bile yönetilen kod uzantılarıyla oluşturulan bir Office çözümü çalışır. Bunun nedeni. .NET derleme kodu güvenliği microsoft .NET Framework tarafından Microsoft Office.

 Ancak, bazen kodu çalıştırmadan bir belgeyi açmak istemeniz gerekir. Örneğin, belge açıldığında çalışan kod içeriği değiştirebilir, ancak kod değiştirilmeden önce belgenin nasıl göründüğünü güncelleştirmek istersiniz. Veya belgeyi içinde belirli bilgilerle birlikte birine göndermek ve kodun çalışmasına ve büyük olasılıkla içeriği değiştirmesi istemeyebilirsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Derleme kodunu çalıştırmadan yönetilen kod uzantıları içeren bir belgeyi veya çalışma kitabını açmanın birkaç yolu vardır.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Shift tuşunu kullanarak derlemeyi atlamak için

- Word ve çalışma kitaplarının belge açılırken  başlatma olayları oluşturmasını önlemek için Shift tuşunu basılı Excel tutarak Dosya menüsünden belge ve çalışma kitaplarını açın. 

    > [!NOTE]
    > Bir belgeyi veya çalışma kitabını Başlarken **bölmeden** açarsanız Shift **tuşunu** basılı tutarak kod atlanmaz. Ayrıca SHIFT tuşunu basılı tutarak, belge açıldıktan sonra olayların ortaya çıkarılamayacak.

     Bu yöntem, kodu çalıştırmadan değişiklik yapmak için bir belgeyi açmak ve önce belgeyi değiştirmek için kullanışlıdır.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Bir derlemeyi yeniden kullanarak veya kaldırarak atlamak için

- Derlemenin bulunduğu bilgisayarda gerekli izinlere sahipsiniz, belge veya çalışma kitabının onu bulmamalarını için derlemeyi yeniden adlandırabilirsiniz veya kaldırabilirsiniz. Bu durum, belge her açıldığında Office neden olur.

     Çözüm birden çok kişi tarafından kullanılıyorsa, bu yöntem çözümün hepsi için çalıştırmasını önler. Kodda veya başvurulan sunucuda bir sorun bulunursa ve tüm kullanıcıların bunu yürütmesini durdurmak istediğinizde bu yararlı olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office çözümlerde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)
