---
title: XSD Görev | Microsoft Docs
description: Bir MSBuild veya sınıf dosyası oluşturan XML Şema Tanımı aracını sarmak xsd.exe XSD görevini nasıl kullandığını öğrenin.
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
ms.openlocfilehash: 9af55b62782a8d10b2e193b29bb9d8fade5b9aad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039897"
---
# <a name="xsd-task"></a>XSD görevi

Bir kaynaktan şema veya sınıfxsd.exe *xml* şema tanımı aracını (xsd.exe) sarmalar.

> [!NOTE]
> 2017'Visual Studio başlayarak,xsd.exeiçin C++ *proje* desteği kullanım dışıdır. GaC'ye el ile uygulama ekleyerek **Microsoft.VisualC.CppCodeProvider** *API'CppCodeProvider.dll* kullanabilirsiniz.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **XSD** görevinin parametreleri açıklandı.

- **AdditionalOptions**

     İsteğe **bağlı Dize** parametresi.

     Komut satırda belirtilen seçeneklerin listesi. Örneğin, / \<option1>  / \<option2>  / \<option#> . Başka bir **XSD** görev parametresi tarafından temsil etmeyen seçenekleri belirtmek için bu parametreyi kullanın.

- **GenerateFromSchema**

  İsteğe **bağlı Dize** parametresi.

  Belirtilen şemadan oluşturulan türleri belirtir.

  Her biri bir XSD seçeneğine karşılık gelen aşağıdaki değerlerden birini belirtin.

  - **sınıflar**  -  **/classes**

  - **veri kümesi**  -  **/dataset**

- **Dil**

     İsteğe **bağlı Dize** parametresi.

     Oluşturulan kod için kullanmak üzere programlama dilini belirtir.

     CS **(varsayılan** olan C#), **VB** (Visual Basic) veya **JS (JScript).** Ayrıca uygulayan bir sınıf için tam bir ad belirtin `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Ad Alanı**

     İsteğe **bağlı Dize** parametresi.

     Oluşturulan türleri için çalışma zamanı ad alanını belirtir.

- **Kaynaklar**

     Gerekli `ITaskItem[]` parametre.

     Görevler tarafından MSBuild kaynak dosya öğeleri içeren bir dizi tanımlar.

- **SuppressStartupBanner**

     İsteğe **bağlı Boole parametresi.**

     ise, `true` görev başlatıldığında telif hakkı ve sürüm numarası iletinin görüntülenmesini önler.

- **TrackerLogDirectory**

     İsteğe **bağlı Dize** parametresi.

     İzleyici günlüğünün dizinini belirtir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
