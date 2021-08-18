---
title: çalışma kitabı yüklenemeyen ActiveX denetimleri içeriyor
description: bir çalışma kitabı yüklenemeyen ActiveX denetimleri içerdiğinde oluşan hatayı nasıl çözebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e89484f9da4868ff04cbaeaa72247e39be147185
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147732"
---
# <a name="the-workbook-contains-activex-controls-that-cannot-be-loaded"></a>çalışma kitabı yüklenemeyen ActiveX denetimleri içeriyor

  "bu projeyi oluşturmak için kullanılan çalışma kitabı tasarımcının yükleyemeyeceği ActiveX denetimleri içerir" bir Word belgesine veya bir Excel çalışma sayfasına program aracılığıyla bir denetim eklediğinizde, belgeyi veya çalışma kitabını kaydettiğinizde ve sonra belge veya çalışma kitabını temel alan yeni bir belge düzeyi çözüm oluşturduğunuzda, tasarımcı tarafından desteklenmeyen denetimler içeriyor.

 Denetimin yönetilen türünü açıklayan bilgiler belge veya çalışma kitabıyla birlikte kaydedilmez. bu belge veya çalışma kitabına dayalı yeni bir çözüm oluşturduğunuzda, Visual Studio konak öğesi tasarımcısında denetimi yüklemek için yeterli bilgiye sahip değildir.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Belgeyi veya çalışma kitabını açın.

2. Çalışma zamanında eklenen denetimleri kaldırın. Bunu belge veya çalışma kitabında seçerek ve **Delete** tuşuna basarak yapabilirsiniz.

3. Belge veya çalışma kitabı temelinde belge düzeyi çözümü oluşturun.

## <a name="see-also"></a>Ayrıca bkz.
- [nasıl yapılır: Visual Studio Office projeler oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [çalışma zamanında Office belgelere denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)
