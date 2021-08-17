---
title: 'nasıl yapılır: kod çalıştırmadan Office çözümlerini açma'
description: Derleme kodunu çalıştırmadan yönetilen kod uzantıları içeren bir belge veya çalışma kitabını nasıl açabileceğiniz hakkında bilgi edinin.
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
ms.openlocfilehash: c20ddd8fbf05422bfbc948449c2cf3265c7e89c4212add41e220e6f04c77304b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394647"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>nasıl yapılır: kod çalıştırmadan Office çözümlerini açma
  son kullanıcının Office uygulamasındaki güvenlik ayarı yüksek olarak ayarlansa bile, yönetilen kod uzantılarıyla oluşturulan Microsoft Office bir çözüm çalışır. bunun nedeni, .net derleme kodu güvenliğinin Microsoft Office tarafından değil Microsoft .NET Framework tarafından yönetilmektedir.

 Ancak, kodu çalıştırmadan bir belgeyi açmak isteyebileceğiniz durumlar vardır. Örneğin, belge açıldığında çalışan kod içerikleri değiştirebilir, ancak kod değiştirilmeden önce belgenin görünme şeklini güncelleştirmek isteyebilirsiniz. Ya da belgeyi içindeki belirli bilgileri bir kişiye göndermek isteyebilirsiniz ve kodun çalıştırılmasını ve muhtemelen içerikleri değiştirmesini istemezsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Derleme kodunu çalıştırmadan yönetilen kod uzantıları içeren bir belge veya çalışma kitabı açmak için birkaç yol vardır.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Shift tuşunu kullanarak derlemeyi atlamak için

- belge açılırken Word ve Excel başlatma olaylarını oluşturmasını engellemek için **shıft** tuşunu basılı tutarken **dosya** menüsünden belge ve çalışma kitaplarını açın.

    > [!NOTE]
    > **Başlarken** görev bölmesinden bir belge veya çalışma kitabı açarsanız, **SHIFT** tuşunu basılı tutmak kodu atlamaz. Ayrıca, SHIFT 'in basılı tutulması, olayların belge açıldıktan sonra oluşturulmasını engellemez.

     Bu yöntem, kod çalıştırmadan ve belgeyi değiştirmeden değişiklik yapmak için bir belge açmak istiyorsanız yararlıdır.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Yeniden adlandırarak veya kaldırarak bir derlemeyi atlamak için

- Derlemenin bulunduğu bilgisayarda gerekli izinleriniz varsa, belge veya çalışma kitabının onu bulamadığı şekilde derlemeyi yeniden adlandırabilir veya kaldırabilirsiniz. Office belge her açıldığında bu hata oluşur.

     Çözüm birden çok kişi tarafından kullanılıyorsa, bu yöntem çözümün tümünün tarafından çalıştırılmasını önler. Bu, kodda veya başvurulan sunucuda bir sorun bulunursa ve tüm kullanıcıların bunu yürütmesini durdurmak istiyorsanız yararlı olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri güvenli hale getirme](../vsto/securing-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)
