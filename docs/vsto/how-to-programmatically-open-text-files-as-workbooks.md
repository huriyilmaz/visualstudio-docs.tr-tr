---
title: 'Nasıl yapılır: program aracılığıyla metin dosyalarını çalışma kitabı olarak açma'
description: Visual Studio 'Yu kullanarak bir metin dosyasını programlı olarak Microsoft Excel çalışma kitabı olarak açma hakkında bilgi edinin.
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
ms.workload:
- office
ms.openlocfilehash: 47582718128fc9818bb42571e3f33c0190a32d9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888751"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Nasıl yapılır: program aracılığıyla metin dosyalarını çalışma kitabı olarak açma
  Bir metin dosyasını çalışma kitabı olarak açabilirsiniz. Açmak istediğiniz metin dosyasının adını geçirmeniz gerekir. Ayrıştırmaya başlamak için kullanılacak satır numarası ve dosyadaki verilerin sütun biçimi gibi çeşitli isteğe bağlı parametreleri belirtebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Örnek
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#80)]

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
