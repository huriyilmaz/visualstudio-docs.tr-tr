---
title: MSBuild Project Dosya | Microsoft Docs
description: Proje dosyasındaki verileri proje alt türü toplama düzeylerinde korumak için IPersistXMLFragment kullanarak verileri kalıcı yapmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a5147eed5026f010811905fa693baccb4352010e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725029"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>MSBuild Proje Dosyasında Verileri Kalıcı Hale Getirme
Bir proje alt türü, daha sonra kullanmak üzere proje dosyasında alt türe özgü verileri kalıcı olarak bulundurma ihtiyacı olabilir. Proje alt türü, aşağıdaki gereksinimleri karşılamak için proje dosyası kalıcılığı kullanır:

1. Projeyi inşaanın bir parçası olarak kullanılan verileri kalıcı olarak kullanın. (Daha fazla bilgi için Microsoft Build Engine bkz. [MSBuild.)](../../msbuild/msbuild.md) Derlemeyle ilgili bilgiler şunları da olabilir:

    1. Yapılandırmadan bağımsız veriler. Başka bir ifadeyle, MSBuild veya eksik koşulları olan öğelerde depolanan veriler.

    2. Yapılandırmaya bağımlı veriler. Başka bir ifadeyle, MSBuild proje yapılandırması için koşullanmış öğelerde depolanan veriler. Örnek:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Derlemeyle ilgili olan verileri kalıcı olarak kalıcı yap. Bu veriler, bir XML şemasına göre doğrulanmaz serbest biçimli XML ile ifadelanabilir.

    1. Yapılandırmadan bağımsız veriler.

    2. Yapılandırmaya bağımlı veriler.

## <a name="persisting-build-related-information"></a>Kalıcı Build-Related Bilgileri
 Proje inşası için yararlı verilerin kalıcılığı, MSBuild. MSBuild sistemi, derlemeyle ilgili bilgilerin ana bir tablosuna sahiptir. Project alt türleri, özellik değerlerini almak ve ayarlamak için bu verilere erişmekle sorumludur. Project alt türleri, kalıcı olacak ek özellikler ekleyerek ve kalıcı olmayacak şekilde özellikleri kaldırarak derlemeyle ilgili veri tablolarını da geliştirebilirsiniz.

 Veri verilerini MSBuild için, bir proje alt türü temel proje sisteminden MSBuild nesnesi aracılığıyla almaktan <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> sorumludur. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> , temel proje sisteminde uygulanan bir arabirimdir ve çalıştırarak bunun için bir proje alt türü sorguları `QueryInterface` toplamasıdır.

 Aşağıdaki yordam, kullanarak bir özelliği kaldırma adımlarını <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> özetler.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Bir proje dosyasından bir MSBuild kaldırmak için

1. Proje `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> alt türü üzerinde çağrısı.

2. kaldırmak <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> `pszPropName` istediğiniz özelliğine ayarlanmış şekilde çağrısı.

### <a name="persisting-non-build-related-information"></a>Derleme Dışı İlgili Bilgileri Kalıcı Yap
 Derlemenin önemli olmadığını proje dosyalarında verilerin kalıcılığı aracılığıyla ele <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> alır.

 Ana <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> nesnede, `project subtype aggregator` nesnede veya `project subtype project configuration` her ikisinde de uygulama gerçekleştirebilirsiniz.

 Aşağıdaki noktalar, derleme dışı ilgili bilgilerin kalıcılığıyla ilgili temel kavramları özetler.

- Temel proje, yapılandırmadan bağımsız verileri yüklemek ve kaydetmek için ana proje alt türüne (yani en dıştaki proje alt türüne) toplayıcı nesnesini ve yapılandırmaya bağımlı verileri yüklemek veya kaydetmek için proje alt türü proje yapılandırma nesnelerini arar.

- Temel proje, her proje alt türü toplama düzeyi için birden çok kez yöntemini çağırır ve her düzey için <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> GUID'i iletir.

- Temel proje, belirli bir proje alt türüne ayrılmış bir XML parçasını geçer veya alır ve toplama düzeyleri arasında durumu kalıcı yapmak için bu mekanizmayı kullanır.

- Temel proje, guid'i geçen en dıştaki proje <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> alt türüne uygulama çağrılır. GUID en dıştaki proje alt türüne aitse, çağrının kendisini işler; aksi takdirde, ÇAĞRıyı bir iç proje alt türüne devreder ve guid'nin karşılık gelen proje alt türü bulunana kadar bu şekilde devam ediyor olur.

- Bir proje alt türü, çağrıyı iç proje alt türüne temsilci olarak devreddikten önce veya sonra XML parçasını da değiştirebilir. Aşağıdaki örnekte, bir proje alt türüne özgü özellikleri içeren bir dosyanın adının bu proje alt türüne geçir olduğu bir proje dosyasından bir alıntı gösterir.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>Ayrıca bkz.
- [Proje Alt Türleri](../../extensibility/internals/project-subtypes.md)
