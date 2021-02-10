---
title: MSBuild’da çözüm filtreleri
description: Çözüm filtrelerini açıklar ve MSBuild ile bir çözüm filtresi dosyası oluşturmayı gösterir.
ms.date: 07/28/2020
ms.topic: reference
helpviewer_keywords:
- MSBuild, solution filters
- solution filters [MSBuild]
author: ghogen
ms.author: ghogen
manager: jmartens
monikerRange: '>= vs-2019'
ms.openlocfilehash: 4a5c764ad9ea4190df5e533926671dbd88c53b8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937842"
---
# <a name="solution-filters-in-msbuild"></a>MSBuild’da çözüm filtreleri

Çözüm filtresi dosyaları, bir Çözümdeki tüm projelerden hangi projelerin derleneceğini veya yükleneceğini belirten *. slnf* uzantılı JSON dosyalarıdır. MSBuild 16,7 ' den başlayarak, çözümü filtreleme etkinken oluşturmak için çözüm filtresi dosyasında MSBuild 'i çağırabilirsiniz. 

> [!NOTE]
> Çözüm filtresi dosyası yüklenecek veya oluşturulacak proje kümesini azaltır ve biçimi basitleştirir. Çözüm dosyası yine de gereklidir.

## <a name="build-a-solution-filter-from-the-command-line"></a>Komut satırından bir çözüm filtresi oluşturma

Komut satırından bir çözüm filtresi dosyası oluşturmak, çözüm dosyası oluşturma ile tam olarak aynı söz dizimini kullanır. Filtreleme etkin olarak oluşturulacak çözüm yerine çözüm filtresi dosyasını aşağıdaki gibi belirtin:

```console
msbuild [options] solutionFilterFile.slnf
```

Ayrıca anahtarlar ve ek özellikleri normal olarak ekleyebilirsiniz. Bkz. [MSBuild komut satırı başvurusu](msbuild-command-line-reference.md). Bu komut filtrelenmiş projeleri ve bağımlı oldukları projeleri oluşturur. Komut satırından bir çözüm filtresi oluştururken, MSBuild otomatik olarak bağımlılıklar ' ı izler. Filtrede belirtilmişse veya oluşturulmuş bir proje tarafından başvuruluyorsa bir proje oluşturur.

## <a name="solution-filter-files"></a>Çözüm filtresi dosyaları

Çözüm filtresi dosyalarıyla çalışmak için Visual Studio 'Yu kullanabilirsiniz. Visual Studio 'da bir çözüm filtresi açmak, yüklenmeyen projelerin yanı sıra yüklü projeleri de görüntüler ve bunları oluşturmak için seçmek üzere daha fazla proje yükleme seçeneği sunar. İlk proje (ler) de derleme için bağlı olan tüm projeleri yükleyebilirsiniz, ancak bu gerekli değildir. [Filtrelenmiş çözümlere](../ide/filtered-solutions.md)bakın.

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

Aşağıda, Visual Studio 'da filtrelenmiş bir çözüme örnek verilmiştir:

![Visual Studio 'da filtrelenmiş çözümün ekran görüntüsü](media/solution-with-filter.png)

Bu çözümde, ClassLibrary1 hem ProjectA hem de ProjectB tarafından kullanılır ve bu nedenle ClassLibrary1 bir proje başvurusu olarak listelenir.

Visual Studio 'nun oluşturduğu çözüm filtresi dosyası aşağıda verilmiştir:

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

Bu örnekte, filtreleme etkin ile oluşturduğunuzda (komutunu kullanarak `MSBuild [options] MyFilter.slnf` ), çözüm filtresi dosyasında açıkça listelendiğinden, MSBuild derlemeleri MyApplication ve ProjectA. ProjectA, ClassLibrary1 'in temel aldığı için, MSBuild derlemeleri oluşturma kapsamında.  ProjectB oluşturulmadı. (Bu tartışma, temiz bir derlemeyi kabul eder. Projeler daha önce oluşturuldıysa, normal kurallar zaten güncel olan projeleri atlamak için geçerlidir.)

## <a name="see-also"></a>Ayrıca bkz.

- [Filtrelenmiş çözümler](../ide/filtered-solutions.md)
- [MSBuild komut satırı başvurusu](msbuild-command-line-reference.md)
