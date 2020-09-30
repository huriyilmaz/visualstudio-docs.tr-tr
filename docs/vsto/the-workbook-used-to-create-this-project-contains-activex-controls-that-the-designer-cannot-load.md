---
title: Çalışma kitabı yüklenemeyen ActiveX denetimleri içeriyor
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: error-reference
f1_keywords:
- VST.SelectDocWizard.ContainsActiveXControls
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 09182fb354ad3ae8937b66952a0acd376d54fe0a
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584457"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>Çalışma kitabı yüklenemeyen ActiveX denetimleri içeriyor

  "Bu projeyi oluşturmak için kullanılan çalışma kitabı tasarımcının yükleyemeyeceği ActiveX denetimleri içeriyor" hatası, bir Word belgesine veya Excel çalışma sayfasına programlı bir şekilde denetim eklediğinizde, belgeyi veya çalışma kitabını kaydettiğinizde ve sonra belge veya çalışma kitabını temel alan yeni bir belge düzeyi çözüm oluşturacak şekilde görünür.

 Denetimin yönetilen türünü açıklayan bilgiler belge veya çalışma kitabıyla birlikte kaydedilmez. Bu belgeye veya çalışma kitabına dayalı yeni bir çözüm oluşturduğunuzda, Visual Studio 'Nun denetimi konak öğesi tasarımcısında yüklemek için yeterli bilgi yok.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Belgeyi veya çalışma kitabını açın.

2. Çalışma zamanında eklenen denetimleri kaldırın. Bunu belge veya çalışma kitabında seçerek ve **Delete** tuşuna basarak yapabilirsiniz.

3. Belge veya çalışma kitabı temelinde belge düzeyi çözümü oluşturun.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Visual Studio 'da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
