---
title: XSD görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0c9dcc0d09887cacca7e6cdaa2e4f2b719c6451c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67826239"
---
# <a name="xsd-task"></a>XSD Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir kaynaktan şema veya sınıf dosyaları üreten XML şema tanımı aracını (xsd.exe) sarmalanmış olarak kaydırır.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda, **XSD** görevinin parametreleri açıklanmaktadır.  
  
- **AdditionalOptions**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Komut satırında belirtilen seçeneklerin listesi. Örneğin, "*/option1/option2/option #*". Başka bir **XSD** görev parametresi tarafından temsil edilmeyen seçenekleri belirtmek için bu parametreyi kullanın.  
  
- **GenerateFromSchema**  
  
  İsteğe bağlı **dize** parametresi.  

  Belirtilen şemadan oluşturulan türleri belirtir.  

  Her biri bir XSD seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.  

  - **sınıflar**  -  **/Classes**  

  - **veri kümesi**  -  **/DataSet**  
  
- **Dil**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Oluşturulan kod için kullanılacak programlama dilini belirtir.  
  
     **CS** (varsayılan olan C#), **vb** (Visual Basic) veya **js** (JScript) arasından seçim yapın. Ayrıca uygulayan bir sınıf için tam bir ad belirtin `System.CodeDom.Compiler.CodeDomProvider Class`.  
  
- **Ad Alanı**  
  
     İsteğe bağlı **dize** parametresi.  
  
     Oluşturulan türleri için çalışma zamanı ad alanını belirtir.  
  
- **Kaynaklar**  
  
     Gerekli `ITaskItem[]` parametre.  
  
     Görevler tarafından tüketilen ve yayılmakta olabilecek bir MSBuild kaynak dosya öğeleri dizisini tanımlar.  
  
- **SuppressStartupBanner**  
  
     İsteğe bağlı **Boolean** parametresi.  
  
     İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.  
  
- **TrackerLogDirectory**  
  
     İsteğe bağlı **dize** parametresi.  
  
     İzleyici günlüğü için dizini belirtir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
