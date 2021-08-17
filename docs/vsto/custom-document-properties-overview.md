---
title: Özel belge özelliklerine genel bakış
description: Belge düzeyi bir proje derlemek için Visual Studio projesinde belgeye iki özel özellik ekleyen bir uygulama olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a7b8b30304ed840843818a4d576fdfdb49bc36b54e72f77f441e1d9864e876c0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424443"
---
# <a name="custom-document-properties-overview"></a>Özel belge özelliklerine genel bakış

Belge düzeyinde bir proje derlemeniz Visual Studio projesinde belgeye iki özel özellik ekler: \_ AssemblyLocation ve \_ AssemblyName. Kullanıcı bir belgeyi açtığında, Microsoft Office bu özel belge özelliklerini denetler. Bunlar belgede mevcutsa, uygulama özelleştirmeyi [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] başlatan uygulamasını yükler. Daha fazla bilgi için [bkz. Office çözüm mimarisi Visual Studio.](../vsto/architecture-of-office-solutions-in-visual-studio.md)

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="_assemblyname"></a>\_Assemblyname

Bu özellik, çözümünün Office bileşeninde bir arabirimin CLSID'lerini [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] içerir. CLSID değeri 4E3C66D5-58D4-491E-A7D4-64AF99AF6E8B'tir. Bu değeri hiçbir zaman değiştirmeysiniz.

## <a name="_assemblylocation"></a>\_AssemblyLocation

Bu özellik, özelleştirme için dağıtım bildirimi hakkında ayrıntılı bilgi sağlayan bir dize içerir. Bildirim hakkında daha fazla bilgi için [bkz. Uygulama ve dağıtım bildirimleri Office.](../vsto/application-and-deployment-manifests-in-office-solutions.md)

 AssemblyLocation \_ özellik değeri, çözümün nasıl dağıtılacağına bağlı olarak farklı biçimlere sahip olabilir:

- Çözüm bir Web sitesinden, UNC yolundan veya bir CD veya USB sürücüsünden yüklenecek şekilde yayımlanırsa, _AssemblyLocation özelliği *DeploymentManifestPath* | *SolutionID biçimindedir.* Aşağıdaki dize bir örnektir:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Çözümü Visual Studio'den çalıştırıyor veya hata ayıklarsanız, _AssemblyLocation özelliği *DeploymentManifestName* | *SolutionID*|vstolocal biçimindedir. Aşağıdaki dize bir örnektir:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9|vstolocal

  *SolutionID,* çözümü tanımlamak için [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] kullanan bir GUID'dir. Projeyi *derlemeniz* sırasında SolutionID otomatik olarak oluşturulur. **vstolocal** terimi, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] derlemenin belgeyle aynı klasörden yükleniyor olması gerektiğini gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözüm mimarisi Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Belge düzeyinde özelleştirmelerin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [Office çözümlerde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Nasıl Office: Office kullanarak bir ClickOnce](/previous-versions/bb386095(v=vs.110))
- [Nasıl kullanılır: Özel belge özellikleri oluşturma ve değiştirme](../vsto/how-to-create-and-modify-custom-document-properties.md)