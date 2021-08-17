---
title: MSBuild’da çözüm filtreleri
description: Çözüm filtrelerini açıklar ve MSBuild bir çözüm filtresi dosyası oluşturmayı gösterir.
ms.date: 07/28/2020
ms.topic: reference
helpviewer_keywords:
- MSBuild, solution filters
- solution filters [MSBuild]
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
monikerRange: '>= vs-2019'
ms.openlocfilehash: a080e6ba9703138d9ad8b6d272f09dd18c65ffb75a35fc2aa8cd42e90d00e172
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427526"
---
# <a name="solution-filters-in-msbuild"></a>MSBuild’da çözüm filtreleri

Çözüm filtresi dosyaları, bir Çözümdeki tüm projelerden hangi projelerin derleneceğini veya yükleneceğini belirten *. slnf* uzantılı JSON dosyalarıdır. MSBuild 16,7 ' den başlayarak, filtre etkin bir çözüm oluşturmak için çözüm filtresi dosyasında MSBuild çağırabilirsiniz. 

> [!NOTE]
> Çözüm filtresi dosyası yüklenecek veya oluşturulacak proje kümesini azaltır ve biçimi basitleştirir. Çözüm dosyası yine de gereklidir.

## <a name="build-a-solution-filter-from-the-command-line"></a>Komut satırından bir çözüm filtresi oluşturma

Komut satırından bir çözüm filtresi dosyası oluşturmak, çözüm dosyası oluşturma ile tam olarak aynı söz dizimini kullanır. Filtreleme etkin olarak oluşturulacak çözüm yerine çözüm filtresi dosyasını aşağıdaki gibi belirtin:

```console
msbuild [options] solutionFilterFile.slnf
```

Ayrıca anahtarlar ve ek özellikleri normal olarak ekleyebilirsiniz. bkz. [MSBuild komut satırı başvurusu](msbuild-command-line-reference.md). Bu komut filtrelenmiş projeleri ve bağımlı oldukları projeleri oluşturur. komut satırından bir çözüm filtresi oluştururken MSBuild bağımlılıkları otomatik olarak izler. Filtrede belirtilmişse veya oluşturulmuş bir proje tarafından başvuruluyorsa bir proje oluşturur.

## <a name="solution-filter-files"></a>Çözüm filtresi dosyaları

çözüm filtresi dosyalarıyla çalışmak için Visual Studio kullanabilirsiniz. Visual Studio bir çözüm filtresi açmak, yüklenmeyen projeleri ve yüklü projeleri görüntüler ve bunları oluşturmak için seçmek üzere daha fazla proje yükleme seçeneği sunar. İlk proje (ler) de derleme için bağlı olan tüm projeleri yükleyebilirsiniz, ancak bu gerekli değildir. [Filtrelenmiş çözümlere](../ide/filtered-solutions.md)bakın.

Çözüm filtresinin, Çözümle aynı klasörde olması gerekmez. Çözüm dosyasının yolu, çözüm filtresi dosyasının konumuyla ilişkilidir, ancak her projenin yolu çözüm dosyasının kendisi ile ilişkilidir ve çözüm dosyasındaki proje yollarıyla eşleşmelidir. Aşağıdaki örnek, göreli yolların kullanımını gösterir:

```json
{
  "solution": {
    "path": "..\\..\\Documents\\GitHub\\msbuild\\MSBuild.sln",
    "projects": [
      "src\\Build.OM.UnitTests\\Microsoft.Build.Engine.OM.UnitTests.csproj"
    ]
  }
}
```

Yollarda ters eğik çizgiler, kaçışlar için iki katına çıkar.

## <a name="example"></a>Örnek

Aşağıda Visual Studio filtrelenmiş bir çözüme örnek verilmiştir:

![Visual Studio filtrelenmiş çözümün ekran görüntüsü](media/solution-with-filter.png)

Bu çözümde, ClassLibrary1 hem ProjectA hem de ProjectB tarafından kullanılır ve bu nedenle ClassLibrary1 bir proje başvurusu olarak listelenir.

Visual Studio oluşturan çözüm filtresi dosyası aşağıda verilmiştir:

```json
{
  "solution": {
    "path": "MyApplication.sln",
    "projects": [
      "MyApplication\\MyApplication.csproj",
      "ProjectA\\ProjectA.csproj"
    ]
  }
}
```

bu örnekte, filtreleme etkin ile oluşturduğunuzda (komutunu kullanarak `MSBuild [options] MyFilter.slnf` ), çözüm filtresi dosyasında açıkça listelendiğinden, MyApplication ve projecta yapılarını MSBuild. ProjectA 'nın ClassLibrary1 derlemesi kapsamında, ProjectA buna bağlı olduğundan MSBuild.  ProjectB oluşturulmadı. (Bu tartışma, temiz bir derlemeyi kabul eder. Projeler daha önce oluşturuldıysa, normal kurallar zaten güncel olan projeleri atlamak için geçerlidir.)

## <a name="see-also"></a>Ayrıca bkz.

- [Filtrelenmiş çözümler](../ide/filtered-solutions.md)
- [komut satırı başvurusunu MSBuild](msbuild-command-line-reference.md)
