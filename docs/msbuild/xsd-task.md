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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 217e045a731efa1fe3ba1dda63e89eca685d4b75
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630788"
---
# <a name="xsd-task"></a>XSD görevi

Bir kaynaktan şema veya sınıf dosyaları üreten XML şema tanımı aracı 'nı (*XSD. exe*) sarmalanmış olarak kaydırır.

> [!NOTE]
> Visual Studio 2017 ' den başlayarak C++ , *XSD. exe* için proje desteği kullanım dışıdır. *Cppcodeprovider. dll dosyasını* el ile GAC 'ye ekleyerek **Microsoft. VisualC. cppcodeprovider** API 'lerini kullanmaya devam edebilirsiniz.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda, **XSD** görevinin parametreleri açıklanmaktadır.

- **AdditionalOptions**

     İsteğe bağlı **dize** parametresi.

     Komut satırında belirtilen seçeneklerin listesi. Örneğin,/\<Seçenek1 >/\<Seçenek2 >/\<Seçenek # >. Başka bir **XSD** görev parametresi tarafından temsil edilmeyen seçenekleri belirtmek için bu parametreyi kullanın.

- **GenerateFromSchema**

  İsteğe bağlı **dize** parametresi.

  Belirtilen şemadan oluşturulan türleri belirtir.

  Her biri bir XSD seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **sınıflar** -  **/Classes**

  - **veri kümesi** -  **/DataSet**

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

     `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.

- **TrackerLogDirectory**

     İsteğe bağlı **dize** parametresi.

     İzleyici günlüğü için dizini belirtir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
