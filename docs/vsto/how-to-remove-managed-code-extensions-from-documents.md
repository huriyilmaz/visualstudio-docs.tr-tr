---
title: 'Nasıl yapabilirsiniz: Belgelerden yönetilen kod uzantılarını kaldırma'
description: Özelleştirme derlemelerini, belge düzeyi özelleştirmenin bir parçası olan belge veya çalışma kitabından program aracılığıyla kaldırma Microsoft Word veya Excel.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cf087b0c9da0197327b2fb548365ce6e4d00d5967be118f211916d6d6df34f81
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121408186"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Nasıl yapabilirsiniz: Belgelerden yönetilen kod uzantılarını kaldırma
  Word veya Microsoft Office için belge düzeyinde özelleştirmenin parçası olan bir belge veya çalışma kitabından özelleştirme derlemelerini program Microsoft Office Excel. Kullanıcılar daha sonra belgeleri açıp içeriği görüntülemeye devam ediyor ancak belgelere ekli özel kullanıcı arabirimi (UI) görüntüleniyor ve kodunuz çalıştırılamayacak.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 özelleştirme derlemesi tarafından sağlanan yöntemlerden `RemoveCustomization` birini kullanarak [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] kaldırebilirsiniz. Hangi yöntemi kullandığınız, özelleştirmeyi çalışma zamanında kaldırmak istediğinize (Word belgesi veya Excel çalışma kitabı açıkken özelleştirmede kod çalıştırarak) veya özelleştirmeyi kapalı bir belgeden veya yüklü yüklü bir sunucuda yer alan bir belgeden kaldırmak Microsoft Office bağlıdır.

## <a name="to-remove-the-customization-assembly-at-run-time"></a>Özelleştirme derlemeyi çalışma zamanında kaldırmak için

1. Özelleştirme kodunda yöntemini <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> (Word için) veya yöntemini <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> (word için) Excel. Bu yöntem ancak özelleştirme artık gerekli olmadığı için çağrılmalı.

     Kodunda bu yöntemi çağırma yöntemi, özelleştirmenizin nasıl kullanılana bağlıdır. Örneğin, müşteriler belgeyi yalnızca belgenin kendisine (özelleştirmeye değil) ihtiyacı olan diğer istemcilere göndermeye hazır olana kadar özelleştirmenizin özelliklerini kullanıyorsa, müşteri tıkladığında çağıran bazı kullanıcı arabirimi `RemoveCustomization` sekleyebilirsiniz. Alternatif olarak, özelleştirmeniz ilk açıldığında belgeyi verilerle doldurmakta ancak özelleştirme doğrudan müşteriler tarafından erişilen başka bir özellik sağlanmıyorsa, özelleştirmeniz belgeyi başlatmayı tamamlar bitirmez RemoveCustomization çağırabilirsiniz.

## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Özelleştirme derlemesi kapalı bir belgeden veya sunucu üzerinde bir belgeden kaldırmak için

1. Konsol uygulaması veya Windows Forms projesi gibi bir Microsoft Office gerektirmeyen bir projede,Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll *derlemesine* bir başvuru ekleyin.

2. Aşağıdaki **imports veya** **using deyimini** kod dosyanın en üstüne ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet1":::

3. sınıfının statik <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> yöntemini <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> çağırma ve parametresi için çözüm belge yolunu belirtme.

     Aşağıdaki kod örneğinde, özelleştirmeyi masaüstünde yer alanWordDocument1.docx *belgeden* kaldırabilirsiniz.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb" id="Snippet2":::

4. Projeyi derleme ve uygulamayı özelleştirmeyi kaldırmak istediğiniz bilgisayarda çalıştırma. Bilgisayarda, Office çalışma zamanı için Visual Studio 2010 Araçları yüklü olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [ServerDocument sınıfını kullanarak bir sunucu üzerinde belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Nasıl kullanılır: Belgelere Yönetilen kod uzantıları ekleme](../vsto/how-to-attach-managed-code-extensions-to-documents.md)
