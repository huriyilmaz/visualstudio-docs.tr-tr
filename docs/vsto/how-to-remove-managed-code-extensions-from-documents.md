---
title: 'Nasıl yapılır: belgelerden yönetilen kod uzantılarını kaldırma'
description: Özelleştirme derlemesini, Microsoft Word veya Excel için belge düzeyi özelleştirmenin parçası olan bir belgeden veya çalışma kitabından program aracılığıyla kaldırma.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 129b1bda44abf7283efe1996f1898491025ee9d9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825452"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Nasıl yapılır: belgelerden yönetilen kod uzantılarını kaldırma
  Özelleştirme derlemesini, Microsoft Office Word veya Microsoft Office Excel için belge düzeyi özelleştirmenin parçası olan bir belge veya çalışma kitabından programlı bir şekilde kaldırabilirsiniz. Kullanıcılar daha sonra belgeleri açabilir ve içeriği görüntüleyebilir, ancak belgelere eklediğiniz herhangi bir özel kullanıcı arabirimi (UI) görünmez ve kodunuz çalışmaz.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Özelleştirme derlemesini `RemoveCustomization` , tarafından sunulan yöntemlerden birini kullanarak kaldırabilirsiniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Hangi yöntemi kullanacağınızı, çalışma zamanında özelleştirmeyi kaldırmak isteyip istemediğinizi (yani, Word belgesi veya Excel çalışma kitabı açıkken özelleştirirken kod çalıştırarak) ya da özelleştirmeyi, kapalı bir belgeden veya Microsoft Office yüklü olmayan bir sunucuda bulunan bir belgeden kaldırmak istediğinize bağlıdır.

## <a name="to-remove-the-customization-assembly-at-run-time"></a>Çalışma zamanında özelleştirme derlemesini kaldırmak için

1. Özelleştirme kodunuzda <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> yöntemini (Word için) veya <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> yöntemini (Excel için) çağırın. Bu yöntem yalnızca özelleştirmeye artık gerek duyulmadığında çağrılmalıdır.

     Kodunuzda bu yöntemi çağırdığınızda özelleştirmenin nasıl kullanıldığına bağlıdır. Örneğin, müşteriler, belgeyi yalnızca belgenin kendisi için ihtiyacı olan diğer istemcilere göndermeye hazırlanana kadar, özelleştirmenin özelliklerini kullanıyorsa, müşterinin tıkladığı zaman çağıran bazı Kullanıcı arabirimini sağlayabilirsiniz `RemoveCustomization` . Alternatif olarak, özelleştirmeniz ilk açıldığında belgeyi veriyle doldurursa, ancak özelleştirme doğrudan müşteriler tarafından erişilen başka herhangi bir özelliği sağlamıyorsa, özelleştirme belgeyi başlatmayı bitirdiğinde, Removeccustombir seçim yapabilirsiniz.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Bir sunucudaki kapalı bir belgeden veya bir belgeden özelleştirme derlemesini kaldırmak için

1. Konsol uygulaması veya Windows Forms projesi gibi Microsoft Office gerektirmeyen bir projede, *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* derlemesine bir başvuru ekleyin.

2. Aşağıdaki **Içeri aktarmaları** veya **using** ifadesini, kod dosyanızın en üstüne ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet1":::

3. <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>Sınıfının statik yöntemini çağırın <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> ve parametresi için çözüm belge yolunu belirtin.

     Aşağıdaki kod örneği, özelleştirmeyi masaüstündeki *WordDocument1.docx* adlı bir belgeden kaldırabildiğinizi varsayar.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet2":::

4. Projeyi derleyin ve özelleştirmeyi kaldırmak istediğiniz bilgisayarda uygulamayı çalıştırın. Bilgisayarda Office Runtime için Visual Studio 2010 Araçları yüklü olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [ServerDocument sınıfını kullanarak bir sunucudaki belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Nasıl yapılır: belgelere yönetilen kod uzantıları Iliştirme](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
