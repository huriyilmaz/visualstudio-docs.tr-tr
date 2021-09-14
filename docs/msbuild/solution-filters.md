---
title: MSBuild’da çözüm filtreleri
description: Çözüm filtrelerini açıklar ve çözüm filtresi dosyası derlemeyi MSBuild.
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
ms.openlocfilehash: a21916045c3a06dba224d4db632bc9332ac6d83b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625509"
---
# <a name="solution-filters-in-msbuild"></a>MSBuild’da çözüm filtreleri

Çözüm filtresi dosyaları, bir çözümde yer alan tüm projelerden hangi projelerin derlemesi veya yüklnf olduğunu belirten *.slnf* uzantısına sahip JSON dosyalarıdır. 16.7 MSBuild den başlayarak, MSBuild etkinleştirilmiş bir çözüm oluşturmak için çözüm filtre dosyasındaki dosyaları çağırabilirsiniz. 

> [!NOTE]
> Çözüm filtresi dosyası yüklenecek veya yapılacak proje kümelerini azaltır ve biçimi basitler. Çözüm dosyası hala gereklidir.

## <a name="build-a-solution-filter-from-the-command-line"></a>Komut satırdan çözüm filtresi oluşturma

Komut satırına bir çözüm filtresi dosyası inşa edildiklerinden, çözüm dosyasıyla tam olarak aynı söz dizimi kullanılır. Filtreleme etkin olarak derlemek için çözüm yerine çözüm filtresi dosyasını aşağıdaki gibi belirtin:

```console
msbuild [options] solutionFilterFile.slnf
```

Ayrıca anahtarları ve ek özellikleri normal şekilde ebilirsiniz. Bkz. [MSBuild satırı başvurusu.](msbuild-command-line-reference.md) Bu komut, filtrelenmiş projeleri ve bağımlı olduğu tüm projeleri derlemeye devam ediyor. Komut satırdan bir çözüm filtresi oluşturulurken, MSBuild otomatik olarak izler. Filtrede belirtilirse veya bir proje tarafından başvurulsa bir proje derlemesi.

## <a name="solution-filter-files"></a>Çözüm filtresi dosyaları

Çözüm filtre Visual Studio çalışmak için bu dosyaları kullanabilirsiniz. Bir çözüm filtresini Visual Studio, yüklenen projelerin yanı sıra kaldırılmış projeleri de görüntüler ve bunları bina için seçmek için daha fazla proje yükleme seçeneği sunar. İlk projelerin derlemeye bağımlı olduğu tüm projeleri de yükleysiniz, ancak bu gerekli değildir. Bkz. [Filtrelenmiş çözümler.](../ide/filtered-solutions.md)

Çözüm filtresinin çözümle aynı klasörde olması gerek değildir. Çözüm dosyasının yolu, çözüm filtresi dosyasının konumuyla görelidir, ancak her projenin yolları çözüm dosyasının kendisine göredir ve çözüm dosyasındaki proje yolları ile eşleşmesi gerekir. Aşağıdaki örnek göreli yolların kullanımını gösteriyor:

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

Yollarda yer alan geri tireler, kaçıldıkları için iki katına çıkar.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, aşağıdaki örnekte filtrelenmiş çözüm Visual Studio:

![Visual Studio'da filtrelenmiş çözümün ekran görüntüsü](media/solution-with-filter.png)

Bu çözümde ClassLibrary1 hem ProjectA hem de ProjectB tarafından kullanılır ve bu nedenle ClassLibrary1 proje başvurusu olarak listelenir.

Oluşturulan çözüm filtresi dosyası Visual Studio:

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

Bu örnekte, filtreleme etkin bir şekilde (komutunu kullanarak) derlemeniz MSBuild çözüm filtre dosyasında açıkça listelenmiş olduğundan `MSBuild [options] MyFilter.slnf` MyApplication ve ProjectA'yı derlemez. ProjectA oluşturmanın bir parçası MSBuild, ProjectA buna bağlı olduğundan ClassLibrary1'i derlemektir.  ProjectB yerleşik değildir. (Bu tartışma temiz bir derleme olduğunu varsayıyor. Projeler daha önce inşa edilmişse, zaten güncel olan projelerin atlanmaları için normal kurallar geçerlidir.)

## <a name="see-also"></a>Ayrıca bkz.

- [Filtrelenmiş çözümler](../ide/filtered-solutions.md)
- [MSBuild satırı başvurusu](msbuild-command-line-reference.md)
