---
title: 'Nasıl yapılır: belgelere yönetilen kod uzantıları Iliştirme'
description: Varolan bir Microsoft Office Word belgesine veya Microsoft Office Excel çalışma kitabına bir özelleştirme derlemesini nasıl ekleyebileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], attaching
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1929daaa82dbfec6f58513bf94eefe01f9520601
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844394"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Nasıl yapılır: belgelere yönetilen kod uzantıları Iliştirme
  Varolan bir Microsoft Office Word belgesine veya Microsoft Office Excel çalışma kitabına bir özelleştirme derlemesi ekleyebilirsiniz. Belge veya çalışma kitabı, Visual Studio 'daki Microsoft Office projeleri ve geliştirme araçları tarafından desteklenen herhangi bir dosya biçiminde olabilir. Daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Bir Word veya Excel belgesine özelleştirme eklemek için, <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> sınıfının yöntemini kullanın <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> . <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Sınıfı Microsoft Office yüklü olmayan bir bilgisayarda çalışacak şekilde tasarlandığından, bu yöntemi doğrudan Microsoft Office geliştirmeyle ilgili olmayan çözümlerde (konsol veya Windows Forms uygulaması gibi) kullanabilirsiniz.

> [!NOTE]
> Kod, belirtilen belgenin sahip olmadığı denetimleri bekliyorsa, özelleştirme yükleme başarısız olur.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Yönetilen kod uzantılarını bir belgeye eklemek için

1. Konsol uygulaması veya Windows Forms projesi gibi Microsoft Office gerektirmeyen bir projede, *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* ve *Microsoft.VisualStudio.Tools.Applications.Runtime.dll* derlemelerine bir başvuru ekleyin.

2. Aşağıdaki **Içeri aktarmaları** veya **using** deyimlerini, kod dosyanızın en üstüne ekleyin.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Statik yöntemi çağırın <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> .

     Aşağıdaki kod örneği <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> aşırı yüklemeyi kullanır. Bu aşırı yükleme, belgenin tam yolunu alır ve <xref:System.Uri> belgeye iliştirmek istediğiniz özelleştirme için dağıtım bildiriminin konumunu belirtir. Bu örnek, **WordDocument1.docx** adlı bir Word belgesinin masaüstünde olduğunu ve dağıtım bildiriminin, aynı zamanda masaüstündeki **Yayımla** adlı bir klasörde bulunduğunu varsayar.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Projeyi derleyin ve özelleştirmeyi eklemek istediğiniz bilgisayarda uygulamayı çalıştırın. Bilgisayarda Office Runtime için Visual Studio 2010 Araçları yüklü olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Nasıl yapılır: belgelerden yönetilen kod uzantılarını kaldırma](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)
