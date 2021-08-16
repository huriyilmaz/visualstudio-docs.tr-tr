---
title: 'Nasıl yapılır: program aracılığıyla metin dosyalarını çalışma kitabı olarak açma'
description: bir metin dosyasını program aracılığıyla Microsoft Excel çalışma kitabı olarak açmak için Visual Studio nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening text files as
- text [Office development in Visual Studio], text files
- text files, opening as workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e132cf1f729a279b13c65e9c3da3305f832dc96cdebf8c4a053264792db0e2f1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121296872"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Nasıl yapılır: program aracılığıyla metin dosyalarını çalışma kitabı olarak açma
  Bir metin dosyasını çalışma kitabı olarak açabilirsiniz. Açmak istediğiniz metin dosyasının adını geçirmeniz gerekir. Ayrıştırmaya başlamak için kullanılacak satır numarası ve dosyadaki verilerin sütun biçimi gibi çeşitli isteğe bağlı parametreleri belirtebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet80":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet80":::

## <a name="compile-the-code"></a>Kodu derle
 Bu örnek aşağıdaki bileşenleri gerektirir:

- Adında `Test.txt` , en az üç satırlık metin içeren bir virgülle ayrılmış metin dosyası.

- `Test.txt`C sürücüsünde depolanacak metin dosyası.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarında çalışma](../vsto/working-with-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını açma](../vsto/how-to-programmatically-open-workbooks.md)
- [Nasıl yapılır: program aracılığıyla yeni çalışma kitapları oluşturma](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını kaydetme](../vsto/how-to-programmatically-save-workbooks.md)
- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını kapatma](../vsto/how-to-programmatically-close-workbooks.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
