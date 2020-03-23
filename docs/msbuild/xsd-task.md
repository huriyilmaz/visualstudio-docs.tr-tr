---
title: XSD Görevi | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630788"
---
# <a name="xsd-task"></a>XSD görevi

Bir kaynaktan şema veya sınıf dosyaları üreten XML Şema Tanımı aracını *(xsd.exe)* sarar.

> [!NOTE]
> Visual Studio 2017'den itibaren *xsd.exe* için C++ proje desteği azalmaktadır. Gac'a *CppCodeProvider.dll'yi* el ile ekleyerek **Microsoft.VisualC.CppCodeProvider** API'lerini kullanmaya devam edebilirsiniz.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **XSD** görevinin parametreleri açıklanmaktadır.

- **Ek Seçenekler**

     İsteğe bağlı **String** parametresi.

     Komut satırında belirtilen seçenekler listesi. Örneğin, /\<option1\<> /\<option2> / seçenek #>. Başka bir **XSD** görev parametresi tarafından temsil edilmeyen seçenekleri belirtmek için bu parametreyi kullanın.

- **Schema'dan Üret**

  İsteğe bağlı **String** parametresi.

  Belirtilen şemadan oluşturulan türleri belirtir.

  Her biri XSD seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **sınıflar** - **/sınıflar**

  - **veri kümesi** - **/veri kümesi**

- **Dil**

     İsteğe bağlı **String** parametresi.

     Oluşturulan kod için kullanılacak programlama dilini belirtir.

     **CS** (Varsayılan olan C#), **VB** (Visual Basic) veya **JS** (JScript) arasından seçim yapın. Ayrıca uygulayan bir sınıf için tam bir ad belirtin `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Namespace**

     İsteğe bağlı **String** parametresi.

     Oluşturulan türleri için çalışma zamanı ad alanını belirtir.

- **Kaynak**

     Gerekli `ITaskItem[]` parametre.

     Görevler tarafından tüketilebilen ve yayılabilen bir dizi MSBuild kaynak dosya öğesi tanımlar.

- **BastırmaBaşlangıç Banner**

     İsteğe bağlı **Boolean** parametresi.

     Eğer, `true`görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.

- **TrackerLogDirectory**

     İsteğe bağlı **String** parametresi.

     İzleyici günlüğüiçin dizini belirtir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
