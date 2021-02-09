---
title: 'Nasıl yapılır: kod çalıştırmadan Office çözümlerini açma'
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
ms.workload:
- office
ms.openlocfilehash: 99f1a01a745544e7e11e724db9c6eafacf0ca201
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876595"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Nasıl yapılır: kod çalıştırmadan Office çözümlerini açma
  Yönetilen kod uzantılarıyla oluşturulan Microsoft Office çözüm, son kullanıcının Office uygulamasındaki güvenlik ayarı yüksek olarak ayarlanmış olsa bile çalıştırılır. Bunun nedeni, .NET derleme kodu güvenliğinin Microsoft Office tarafından değil Microsoft .NET Framework tarafından yönetilmektedir.

 Ancak, kodu çalıştırmadan bir belgeyi açmak isteyebileceğiniz durumlar vardır. Örneğin, belge açıldığında çalışan kod içerikleri değiştirebilir, ancak kod değiştirilmeden önce belgenin görünme şeklini güncelleştirmek isteyebilirsiniz. Ya da belgeyi içindeki belirli bilgileri bir kişiye göndermek isteyebilirsiniz ve kodun çalıştırılmasını ve muhtemelen içerikleri değiştirmesini istemezsiniz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Derleme kodunu çalıştırmadan yönetilen kod uzantıları içeren bir belge veya çalışma kitabı açmak için birkaç yol vardır.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Shift tuşunu kullanarak derlemeyi atlamak için

- Belge açılırken Word ve Excel 'in başlatma olaylarını oluşturmasını engellemek için **SHIFT** tuşunu basılı tutarken **Dosya** menüsünden Belge ve çalışma kitaplarını açın.

    > [!NOTE]
    > **Başlarken** görev bölmesinden bir belge veya çalışma kitabı açarsanız, **SHIFT** tuşunu basılı tutmak kodu atlamaz. Ayrıca, SHIFT 'in basılı tutulması, olayların belge açıldıktan sonra oluşturulmasını engellemez.

     Bu yöntem, kod çalıştırmadan ve belgeyi değiştirmeden değişiklik yapmak için bir belge açmak istiyorsanız yararlıdır.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Yeniden adlandırarak veya kaldırarak bir derlemeyi atlamak için

- Derlemenin bulunduğu bilgisayarda gerekli izinleriniz varsa, belge veya çalışma kitabının onu bulamadığı şekilde derlemeyi yeniden adlandırabilir veya kaldırabilirsiniz. Bu, Office belgesi her açıldığında bir hata oluşunca oluşur.

     Çözüm birden çok kişi tarafından kullanılıyorsa, bu yöntem çözümün tümünün tarafından çalıştırılmasını önler. Bu, kodda veya başvurulan sunucuda bir sorun bulunursa ve tüm kullanıcıların bunu yürütmesini durdurmak istiyorsanız yararlı olabilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)
