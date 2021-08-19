---
title: Bir Office dağıtma
description: Office çözümlerini ClickOnce veya Windows Installer kullanarak dağıtabilirsiniz. Bu ClickOnce kullanarak çözüm dağıtımı için gereken adım sayısını azaltabilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 2345e66ac6d13e4110db7b660d227963bf7abae1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130682"
---
# <a name="deploy-an-office-solution"></a>Bir Office dağıtma
  Office çözümlerini ClickOnce veya Windows Installer kullanarak dağıtabilirsiniz. ClickOnce kullandığınızda, çözümünüzü dağıtmak ve güncelleştirmek için gerekli adımların sayısını azaltmış olursunuz. Windows Installer kullanırsanız, çözümün nasıl yükleneceği ve kullanıcı çözümünüzü yüklediğinde kurulum programının hangi sayfaları görüntüleyeceği üzerinde denetim sahibi olursunuz.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="deploy-a-solution-by-using-clickonce"></a>ClickOnce kullanarak çözüm ClickOnce
 Bir çözümü ClickOnce kullanarak dağıtırken, kullanıcıların yükleyip çalıştırabileceği merkezi bir konumda çözümü yayınlarsınız. Kullanıcılara yeni bir kurulum programı dağıtmaya gerek kalmadan çözümü güncelleştirebilirsiniz.  Bu dağıtım seçeneği daha basittir, ancak özel kurulum sayfalarını kullanıcılara gösteremezsiniz. Ayrıca çözümlerin, birden fazla kullanıcısı olan bilgisayarlara birden fazla kez yüklenmesi gerekir. Bkz. [Office kullanarak bir ClickOnce.](../vsto/deploying-an-office-solution-by-using-clickonce.md)

## <a name="deploy-a-solution-by-using-windows-installer"></a>Windows Installer'ı kullanarak çözüm dağıtma
 Çözümü Windows Installer kullanarak dağıtırken, kullanıcılara bir kurulum programı dağıtırsınız ve kullanıcılar da bu programı kullanarak çözümü yükler. Kurulum programı, çözümü yalnızca geçerli kullanıcı için yüklemek yerine, bir bilgisayarın tüm kullanıcıları için aynı anda yükleyebilir. Çözümünüzü bilgisayarlarına yüklediklerinde kullanıcıların göreceği seçenekler üzerinde biraz daha fazla denetim sahibi olursunuz. Örneğin, bir lisans sözleşmesi gösterebilir veya kullanıcıların çözüme ait belirli bileşenleri yüklemelerine olanak sağlayabilirsiniz. Ancak, çözümü güncelleştirecek olursanız yeni bir kurulum programı dağıtmanız gerekir. Bkz. [Office Yükleyicisi kullanarak Windows dağıtma.](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [Office kullanarak bir çözüm ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Windows Yükleyicisi'Office bir Windows dağıtma](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)
- [Çözüm Office sorunlarını giderme](../vsto/troubleshooting-office-solution-deployment.md)
