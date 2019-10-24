---
title: XSD görevi | Microsoft Docs
ms.date: 06/27/2018
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
- XSD task (MSBuild (C++))
- MSBuild (C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec51406aec9aec8981e5517480e4cd07bc80ffb1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748020"
---
# <a name="xsd-task"></a>XSD görevi
Bir kaynaktan şema veya sınıf dosyaları üreten XML şema tanımı aracı 'nı (*XSD. exe*) sarmalanmış olarak kaydırır.

> [!NOTE]
> Visual Studio 2017 ' den başlayarak C++ , *XSD. exe* için proje desteği kullanım dışıdır. *Cppcodeprovider. dll dosyasını* el ile GAC 'ye ekleyerek **Microsoft. VisualC. cppcodeprovider** API 'lerini kullanmaya devam edebilirsiniz.

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda, **XSD** görevinin parametreleri açıklanmaktadır.

- **AdditionalOptions**

     İsteğe bağlı **dize** parametresi.

     Komut satırında belirtilen seçeneklerin listesi. Örneğin,/\<option1 >/\<option2 >/\<option # >. Başka bir **XSD** görev parametresi tarafından temsil edilmeyen seçenekleri belirtmek için bu parametreyi kullanın.

- **GenerateFromSchema**

  İsteğe bağlı **dize** parametresi.

  Belirtilen şemadan oluşturulan türleri belirtir.

  Her biri bir XSD seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **sınıflar**  -  **/Classes**

  - **veri kümesi**  -  **/DataSet**

- **Dil**

     İsteğe bağlı **dize** parametresi.

     Oluşturulan kod için kullanılacak programlama dilini belirtir.

     **CS** C#(varsayılan olan), **vb** (Visual Basic) veya **js** (JScript) arasından seçim yapın. Ayrıca uygulayan bir sınıf için tam bir ad belirtin `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Uzayına**

     İsteğe bağlı **dize** parametresi.

     Oluşturulan türleri için çalışma zamanı ad alanını belirtir.

- **Ğına**

     Gerekli `ITaskItem[]` parametresi.

     Görevler tarafından tüketilen ve yayılmakta olabilecek bir MSBuild kaynak dosya öğeleri dizisini tanımlar.

- **SuppressStartupBanner**

     İsteğe bağlı **Boolean** parametresi.

     @No__t_0, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.

- **TrackerLogDirectory**

     İsteğe bağlı **dize** parametresi.

     İzleyici günlüğü için dizini belirtir.

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
