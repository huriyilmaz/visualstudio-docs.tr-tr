---
title: MSBuild proje dosyasındaki verileri kalıcı hale getirme | Microsoft Docs
description: Proje dosyasında verileri kalıcı hale getirme ve proje dosyası toplama düzeylerinde verileri sürdürmek için IPersistXMLFragment kullanma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5e2cf082e4ca6a45bf42bd66ce34111d5c056787
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095023"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>MSBuild Proje Dosyasında Verileri Kalıcı Hale Getirme
Bir proje alt türünün, daha sonra kullanmak üzere, alt türe özgü verileri proje dosyasında kalıcı hale getirmeniz gerekebilir. Proje alt türü, aşağıdaki gereksinimleri karşılamak için proje dosyası kalıcılığını kullanır:

1. Projeyi oluşturmanın bir parçası olarak kullanılan verileri kalıcı hale getirin. (Microsoft Build Engine hakkında daha fazla bilgi için bkz. [MSBuild](../../msbuild/msbuild.md).) Derlemeden ilgili bilgiler şunlardan biri olabilir:

    1. Yapılandırmaya bağımsız veriler. Diğer bir deyişle, boş veya eksik koşullara sahip MSBuild öğelerinde depolanan veriler.

    2. Yapılandırmaya bağlı veriler. Diğer bir deyişle, belirli bir proje yapılandırması için koşullu olan MSBuild öğelerinde depolanan veriler. Örnek:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Derleme için uygun olmayan verileri kalıcı hale getirin. Bu veriler, bir XML şemasına göre doğrulanmamış serbest biçimli XML 'de ifade edilebilir.

    1. Yapılandırmaya bağımsız veriler.

    2. Yapılandırmaya bağlı veriler.

## <a name="persisting-build-related-information"></a>Build-Related bilgileri kalıcı hale getirme
 Bir proje oluşturmak için faydalı verilerin kalıcılığı MSBuild aracılığıyla işlenir. MSBuild sistemi, derleme ile ilgili bilgilerin ana tablosunu tutar. Proje alt türleri, özellik değerlerini almak ve ayarlamak için bu verilere erişmenin sorumluluğundadır. Proje alt türleri ayrıca, kalıcı olacak ek özellikler ekleyerek ve kalıcı olmadıkları için özellikleri kaldırarak derleme ile ilgili veri tablosunu da artırabilir.

 MSBuild verilerini değiştirmek için bir proje alt türü, ile temel proje sisteminden MSBuild özellik nesnesini almaktan sorumludur <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> , temel proje sisteminde uygulanan bir arabirimdir ve, toplanan proje alt türü tarafından çalıştırılarak sorgular `QueryInterface` .

 Aşağıdaki yordamda, kullanarak bir özelliği kaldırma adımları özetlenmektedir <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> .

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>MSBuild proje dosyasından bir özelliği kaldırmak için

1. `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> Proje alt türü üzerinde çağrı.

2. Öğesini <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> `pszPropName` kaldırmak istediğiniz özelliğe ayarlayın.

### <a name="persisting-non-build-related-information"></a>Derleme dışı Ilgili bilgileri kalıcı hale getirme
 Derleme önemi olmayan proje dosyalarındaki verilerin kalıcılığını aracılığıyla ele alınır <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> .

 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>Ana `project subtype aggregator` nesne, `project subtype project configuration` nesne veya her ikisine de uygulayabilirsiniz.

 Aşağıdaki noktalara, derleme olmayan ilgili bilgilerin sürekliliği ile ilgili başlıca kavramlar ana hatlarıyla verilmiştir.

- Temel proje, yapılandırmaya bağlı verileri yüklemek veya kaydetmek için ana proje alt türü (yani, en dıştaki proje alt türü) toplayıcı nesnesi ve proje alt türü proje yapılandırma nesneleri üzerinde çağrılır.

- Temel proje <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> her bir proje alt tür toplaması için birden çok kez yöntemini çağırır ve her düzey IÇIN GUID 'yi geçirir.

- Temel proje, belirli bir proje alt türüne ayrılmış bir XML parçasını geçirir veya alır ve bu mekanizmayı toplama düzeyleri arasındaki kalıcı durum olarak kullanır.

- Temel proje, bir GUID içinde geçen en dıştaki proje alt türünün <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> uygulamasını çağırır. GUID en dıştaki proje alt türüne aitse, çağrıyı işler. Aksi halde, bir iç proje alt türüne çağrı atar ve bu, GUID 'ye karşılık gelen proje alt türü bulunana kadar bu şekilde devam eder.

- Bir proje alt türü Ayrıca, bir iç proje alt türüne çağrı temsilcince veya sonrasında XML parçasını değiştirebilir. Aşağıdaki örnek, proje alt türüne özgü özellikleri içeren bir dosyanın adının bu proje alt türüne geçirildiği bir proje dosyasındaki bir alıntıyı gösterir.

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
