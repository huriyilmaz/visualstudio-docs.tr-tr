---
title: Office çözümünü dağıtma
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24ec10c42935ac961218f910fbef98d51f5f5569
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79416516"
---
# <a name="deploy-an-office-solution"></a>Office çözümünü dağıtma
  Office çözümlerini ClickOnce veya Windows Installer kullanarak dağıtabilirsiniz. ClickOnce kullandığınızda, çözümünüzü dağıtmak ve güncelleştirmek için gerekli adımların sayısını azaltmış olursunuz. Windows Installer kullanırsanız, çözümün nasıl yükleneceği ve kullanıcı çözümünüzü yüklediğinde kurulum programının hangi sayfaları görüntüleyeceği üzerinde denetim sahibi olursunuz.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="deploy-a-solution-by-using-clickonce"></a>ClickOnce kullanarak bir çözüm dağıtma
 Bir çözümü ClickOnce kullanarak dağıtırken, kullanıcıların yükleyip çalıştırabileceği merkezi bir konumda çözümü yayınlarsınız. Kullanıcılara yeni bir kurulum programı dağıtmaya gerek kalmadan çözümü güncelleştirebilirsiniz.  Bu dağıtım seçeneği daha basittir, ancak özel kurulum sayfalarını kullanıcılara gösteremezsiniz. Ayrıca çözümlerin, birden fazla kullanıcısı olan bilgisayarlara birden fazla kez yüklenmesi gerekir. Bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploy-a-solution-by-using-windows-installer"></a>Windows Installer kullanarak bir çözüm dağıtma
 Çözümü Windows Installer kullanarak dağıtırken, kullanıcılara bir kurulum programı dağıtırsınız ve kullanıcılar da bu programı kullanarak çözümü yükler. Kurulum programı, çözümü yalnızca geçerli kullanıcı için yüklemek yerine, bir bilgisayarın tüm kullanıcıları için aynı anda yükleyebilir. Çözümünüzü bilgisayarlarına yüklediklerinde kullanıcıların göreceği seçenekler üzerinde biraz daha fazla denetim sahibi olursunuz. Örneğin, bir lisans sözleşmesi gösterebilir veya kullanıcıların çözüme ait belirli bileşenleri yüklemelerine olanak sağlayabilirsiniz. Ancak, çözümü güncelleştirecek olursanız yeni bir kurulum programı dağıtmanız gerekir. Bkz. [Windows Installer kullanarak Office çözümünü dağıtma](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
- [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Windows Installer kullanarak bir Office çözümünü dağıtma](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)
- [Office çözüm dağıtımı sorunlarını giderme](../vsto/troubleshooting-office-solution-deployment.md)
