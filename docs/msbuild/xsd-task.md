---
title: XSD görevi | Microsoft Docs
description: MSBuild, bir kaynaktan şema veya sınıf dosyaları oluşturan xsd.exe XML şema tanımı aracını kaydırmak için XSD görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5885add3c772bf3b2e42b556199fda3deb83426c55dccb3b5eb908a217e9efca
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369390"
---
# <a name="xsd-task"></a>XSD görevi

Bir kaynaktan şema veya sınıf dosyaları üreten XML şema tanımı aracını (*xsd.exe*) sarmalanmış olarak kaydırır.

> [!NOTE]
> Visual Studio 2017 ' den başlayarak *xsd.exe* için C++ proje desteği kullanım dışıdır. GAC 'ye *CppCodeProvider.dll* El Ile ekleyerek **Microsoft. VisualC. CppCodeProvider** API 'lerini kullanmaya devam edebilirsiniz.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda, **XSD** görevinin parametreleri açıklanmaktadır.

- **AdditionalOptions**

     İsteğe bağlı **dize** parametresi.

     Komut satırında belirtilen seçeneklerin listesi. Örneğin,/ \<option1>  / \<option2>  / \<option#> . Başka bir **XSD** görev parametresi tarafından temsil edilmeyen seçenekleri belirtmek için bu parametreyi kullanın.

- **GenerateFromSchema**

  İsteğe bağlı **dize** parametresi.

  Belirtilen şemadan oluşturulan türleri belirtir.

  Her biri bir XSD seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **sınıflar**  -  **/Classes**

  - **veri kümesi**  -  **/DataSet**

- **Dil**

     İsteğe bağlı **dize** parametresi.

     Oluşturulan kod için kullanılacak programlama dilini belirtir.

     **CS** (varsayılan olan C#), **VB** (Visual Basic) veya **JS** (JScript) arasından seçim yapın. Ayrıca uygulayan bir sınıf için tam bir ad belirtin `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Ad Alanı**

     İsteğe bağlı **dize** parametresi.

     Oluşturulan türleri için çalışma zamanı ad alanını belirtir.

- **Kaynaklar**

     Gerekli `ITaskItem[]` parametre.

     görevler tarafından tüketilen ve yayılan MSBuild kaynak dosya öğelerinin dizisini tanımlar.

- **SuppressStartupBanner**

     İsteğe bağlı **Boolean** parametresi.

     İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.

- **TrackerLogDirectory**

     İsteğe bağlı **dize** parametresi.

     İzleyici günlüğü için dizini belirtir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
