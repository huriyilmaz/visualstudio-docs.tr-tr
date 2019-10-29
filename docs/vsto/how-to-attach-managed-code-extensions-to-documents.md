---
title: 'Nasıl yapılır: belgelere yönetilen kod uzantıları Iliştirme'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 8fb212f9c5441d697cfa92feee7dc18fab9270d2
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985971"
---
# <a name="how-to-attach-managed-code-extensions-to-documents"></a>Nasıl yapılır: belgelere yönetilen kod uzantıları Iliştirme
  Varolan bir Microsoft Office Word belgesine veya Microsoft Office Excel çalışma kitabına bir özelleştirme derlemesi ekleyebilirsiniz. Belge veya çalışma kitabı, Visual Studio 'daki Microsoft Office projeleri ve geliştirme araçları tarafından desteklenen herhangi bir dosya biçiminde olabilir. Daha fazla bilgi için bkz. [belge düzeyi özelleştirmelerinin mimarisi](../vsto/architecture-of-document-level-customizations.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Bir Word veya Excel belgesine özelleştirme eklemek için <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfının <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> yöntemini kullanın. <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfı Microsoft Office yüklü olmayan bir bilgisayarda çalışacak şekilde tasarlandığından, bu yöntemi, doğrudan Microsoft Office geliştirmeyle ilgili olmayan çözümlerde (konsol veya Windows Forms uygulaması gibi) kullanabilirsiniz.

> [!NOTE]
> Kod, belirtilen belgenin sahip olmadığı denetimleri bekliyorsa, özelleştirme yükleme başarısız olur.

### <a name="to-attach-managed-code-extensions-to-a-document"></a>Yönetilen kod uzantılarını bir belgeye eklemek için

1. Konsol uygulaması veya Windows Forms projesi gibi Microsoft Office gerektirmeyen bir projede, *Microsoft. VisualStudio. Tools. Applications. ServerDocument. dll* dosyasına bir başvuru ekleyin ve  *Microsoft. VisualStudio. Tools. Applications. Runtime. dll* derlemeleri.

2. Aşağıdaki **Içeri aktarmaları** veya **using** deyimlerini, kod dosyanızın en üstüne ekleyin.

     [!code-csharp[Trin_VstcoreDeployment#4](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#4)]
     [!code-vb[Trin_VstcoreDeployment#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#4)]

3. Statik <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> yöntemini çağırın.

     Aşağıdaki kod örneği <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> aşırı yüklemeyi kullanır. Bu aşırı yükleme, belgenin tam yolunu ve belgeye iliştirmek istediğiniz özelleştirme için dağıtım bildiriminin konumunu belirten bir <xref:System.Uri> alır. Bu örnekte, **WordDocument1. docx** adlı bir Word belgesinin masaüstünde olduğu ve dağıtım bildiriminin de aynı zamanda masaüstündeki **Yayımla** adlı bir klasörde bulunduğu varsayılmaktadır.

     [!code-csharp[Trin_VstcoreDeployment#3](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#3)]
     [!code-vb[Trin_VstcoreDeployment#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#3)]

4. Projeyi derleyin ve özelleştirmeyi eklemek istediğiniz bilgisayarda uygulamayı çalıştırın. Bilgisayarda Office Runtime için Visual Studio 2010 Araçları yüklü olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Nasıl yapılır: belgelerden yönetilen kod uzantılarını kaldırma](../vsto/how-to-remove-managed-code-extensions-from-documents.md)
- [Office çözümlerinde uygulama ve dağıtım bildirimleri](../vsto/application-and-deployment-manifests-in-office-solutions.md)
