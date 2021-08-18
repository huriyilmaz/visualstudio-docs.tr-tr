---
title: 'Nasıl kullanılır: Program aracılığıyla metin dosyalarını çalışma kitapları olarak açma'
description: Bir metin dosyasını program Visual Studio çalışma kitabı olarak açmak için Microsoft Excel öğrenin.
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
ms.openlocfilehash: 68ee509eca06d6785f47fc776ad42c9f010b5219
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106048"
---
# <a name="how-to-programmatically-open-text-files-as-workbooks"></a>Nasıl kullanılır: Program aracılığıyla metin dosyalarını çalışma kitapları olarak açma
  Bir metin dosyasını çalışma kitabı olarak açabilirsiniz. Açmak istediğiniz metin dosyasının adını geçmelisiniz. Hangi satır numarasının ayrıştırmaya başlayacağı ve dosyadaki verilerin sütun biçimi gibi birkaç isteğe bağlı parametre belirtebilirsiniz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="example"></a>Örnek
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet80":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet80":::

## <a name="compile-the-code"></a>Kodu derleme
 Bu örnek aşağıdaki bileşenleri gerektirir:

- En az üç satır metin içeren adlı `Test.txt` virgülle ayrılmış bir metin dosyası.

- `Test.txt`C sürücüsünde depolanmış metin dosyası.

## <a name="see-also"></a>Ayrıca bkz.
- [Çalışma kitaplarıyla çalışma](../vsto/working-with-workbooks.md)
- [Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını açma](../vsto/how-to-programmatically-open-workbooks.md)
- [Nasıl musunuz: Program aracılığıyla yeni çalışma kitapları oluşturma](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını kaydetme](../vsto/how-to-programmatically-save-workbooks.md)
- [Nasıl yapılanlar: Program aracılığıyla çalışma kitaplarını kapatma](../vsto/how-to-programmatically-close-workbooks.md)
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)
