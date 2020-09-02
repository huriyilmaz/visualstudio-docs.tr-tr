---
title: Özel belge özelliklerine genel bakış
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b3f4038a05478d8e2d747efa700c7ece02e4827
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62951173"
---
# <a name="custom-document-properties-overview"></a>Özel belge özelliklerine genel bakış

Belge düzeyinde bir proje oluşturduğunuzda, Visual Studio projedeki belgeye iki özel özellik ekler: \_ AssemblyLocation ve \_ AssemblyName. Bir Kullanıcı bir belge açtığında, Microsoft Office uygulaması bu özel belge özelliklerini denetler. Belgede varsa, uygulama [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] özelleştirmeyi başlatan öğesini yükler. Daha fazla bilgi için bkz. [Visual Studio 'Da Office çözümlerinin mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="_assemblyname"></a>\_AssemblyName

Bu özellik, öğesinin Office çözüm yükleyicisi bileşenindeki bir arabirimin CLSID 'sini içerir [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . CLSID değeri 4E3C66D5-58D4-491E-A7D4-64AF99AF6E8B. Bu değeri asla değiştirmemelisiniz.

## <a name="_assemblylocation"></a>\_AssemblyLocation

Bu özellik özelleştirme için dağıtım bildirimiyle ilgili ayrıntıları sağlayan bir dize içerir. Bildirimler hakkında daha fazla bilgi için bkz. [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 \_AssemblyLocation Özellik değeri, çözümün nasıl dağıtıldığına bağlı olarak farklı biçimlere sahip olabilir:

- Çözüm bir Web sitesinden, UNC yolundan veya CD ya da USB sürücüsünden yüklenmek üzere yayımlandıysa, _AssemblyLocation özelliği *DeploymentManifestPath* | *SolutionId*biçimindedir. Aşağıdaki dize bir örnektir:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Visual Studio 'da çözümü çalıştırıyorsanız veya hata ayıklaması yapıyorsanız, _AssemblyLocation özelliği *DeploymentManifestName* | *SolutionId*| vstolocal biçimindedir. Aşağıdaki dize bir örnektir:

     ExcelWorkbook1. VSTO | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal

  *SolutionId* , [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] çözümü tanımlamak IÇIN kullandığı bir GUID 'dir. *Çözüm Kimliği* , projeyi oluşturduğunuzda otomatik olarak oluşturulur. **Vstolocal** terimi, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] derlemenin belgeyle aynı klasörden yüklenmesi gerektiğini gösterir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da Office çözümlerinin mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md)
- [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Nasıl yapılır: ClickOnce kullanarak bir Office çözümünü yayımlama](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Nasıl yapılır: özel belge özelliklerini oluşturma ve değiştirme](../vsto/how-to-create-and-modify-custom-document-properties.md)
