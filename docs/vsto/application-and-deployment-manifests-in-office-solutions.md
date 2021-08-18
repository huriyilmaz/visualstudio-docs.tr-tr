---
title: Office çözümlerinde uygulama ve dağıtım bildirimleri
description: uygulama bildiriminin, derlemelerini bulmak ve güncelleştirmek için bir Office çözümü tarafından kullanılan bilgileri sağlayan bir XML dosyası olduğunu öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9143a67064715fc926ddec1e2bb68301982ff928
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038259"
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Office çözümlerinde uygulama ve dağıtım bildirimleri
  uygulama bildirimi, derlemelerini bulmak ve güncellemek için bir Office çözümü tarafından kullanılan bilgileri sağlayan bir XML dosyasıdır. Uygulama bildirimi, uygulama bildirimi ve derlemelerinin en güncel sürümünü bulmak için gereken bilgileri sağlayan, sunucuda depolanan bir XML dosyası olan dağıtım bildirimiyle birlikte kullanılabilir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="manifest-structure-for-office-solutions"></a>Office çözümleri için bildirim yapısı
 Visual Studio Office geliştirme araçları kullanılarak oluşturulan Microsoft Office çözümleri için, tüm bildirimler standart ClickOnce şemasını temel alır. Office çözümlerinizi dağıttığınızda, hem belge düzeyi hem de VSTO eklenti projelerinin uygulama bildirimleri ClickOnce önbelleğinde bulunur. Dağıtım bildirimleri istemci bilgisayara kopyalanmaz.

 Office projelerine yönelik uygulama ve dağıtım bildirimlerinin içerikleri hakkında daha fazla bilgi için, bkz. [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md) ve [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md).

## <a name="create-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimleri oluşturma
 Uygulama bildirimleri, yapı sürecinin bir parçası olarak otomatik olarak oluşturulur. Belge düzeyinde bir proje oluşturduğunuzda, dağıtım bildiriminin konumu belgeye özel belge özelliği olarak katıştırılır. VSTO eklentiler için, dağıtım bildiriminin konumu kayıt defterinde saklanır.

 **yayımlama sihirbazı** hakkında daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md).

 bildirimlerin Office çözümlerle nasıl çalıştığı hakkında daha fazla bilgi için bkz. [Deploy a Office solution](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [VSTO Eklentileri Mimarisi](../vsto/architecture-of-vsto-add-ins.md)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)