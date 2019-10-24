---
title: MSBuild proje dosyasındaki verileri kalıcı hale getirme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7772f633c44c50b24995b7cc8a3f2f8bbbb01863
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726061"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>MSBuild Proje Dosyasında Verileri Kalıcı Hale Getirme
Bir proje alt türünün, daha sonra kullanmak üzere, alt türe özgü verileri proje dosyasında kalıcı hale getirmeniz gerekebilir. Proje alt türü, aşağıdaki gereksinimleri karşılamak için proje dosyası kalıcılığını kullanır:

1. Projeyi oluşturmanın bir parçası olarak kullanılan verileri kalıcı hale getirin. (Microsoft Build Engine hakkında daha fazla bilgi için bkz. [MSBuild](../../msbuild/msbuild.md).) Derlemeden ilgili bilgiler şunlardan biri olabilir:

    1. Yapılandırmaya bağımsız veriler. Diğer bir deyişle, boş veya eksik koşullara sahip MSBuild öğelerinde depolanan veriler.

    2. Yapılandırmaya bağlı veriler. Diğer bir deyişle, belirli bir proje yapılandırması için koşullu olan MSBuild öğelerinde depolanan veriler. Örneğin:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Derleme için uygun olmayan verileri kalıcı hale getirin. Bu veriler, bir XML şemasına göre doğrulanmamış serbest biçimli XML 'de ifade edilebilir.

    1. Yapılandırmaya bağımsız veriler.

    2. Yapılandırmaya bağlı veriler.

## <a name="persisting-build-related-information"></a>Derleme ile Ilgili kalıcı bilgiler
 Bir proje oluşturmak için faydalı verilerin kalıcılığı MSBuild aracılığıyla işlenir. MSBuild sistemi, derleme ile ilgili bilgilerin ana tablosunu tutar. Proje alt türleri, özellik değerlerini almak ve ayarlamak için bu verilere erişmenin sorumluluğundadır. Proje alt türleri ayrıca, kalıcı olacak ek özellikler ekleyerek ve kalıcı olmadıkları için özellikleri kaldırarak derleme ile ilgili veri tablosunu da artırabilir.

 MSBuild verilerini değiştirmek için bir proje alt türü, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> aracılığıyla temel proje sisteminden MSBuild özellik nesnesini almaktan sorumludur. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>, temel proje sisteminde uygulanan bir arabirimdir ve toplanan proje alt türü, `QueryInterface` çalıştırılarak sorgular.

 Aşağıdaki yordamda <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> kullanarak bir özelliği kaldırma adımları özetlenmektedir.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>MSBuild proje dosyasından bir özelliği kaldırmak için

1. Proje alt türünün <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> `QueryInterface` çağırın.

2. Kaldırmak istediğiniz özelliği `pszPropName` ayarlanmış <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> çağırın.

### <a name="persisting-non-build-related-information"></a>Derleme dışı Ilgili bilgileri kalıcı hale getirme
 Derleme önemi olmayan proje dosyalarındaki verilerin kalıcılığı <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> aracılığıyla işlenir.

 @No__t_0 ana `project subtype aggregator` nesnesi, `project subtype project configuration` nesnesi veya her ikisi üzerinde de uygulayabilirsiniz.

 Aşağıdaki noktalara, derleme olmayan ilgili bilgilerin sürekliliği ile ilgili başlıca kavramlar ana hatlarıyla verilmiştir.

- Temel proje, ana proje alt türüne (yani, en dıştaki proje alt türü), yapılandırma bağımsız verilerini yüklemek ve kaydetmek için toplayıcı nesnesini çağırır ve yapılandırmaya bağlı olarak yüklemek veya kaydetmek için proje alt türü proje yapılandırma nesnelerinde çağrılır verileri.

- Temel proje, her bir proje alt tür toplaması için birden çok kez <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> yöntemini çağırır ve her düzey için GUID 'YI geçirir.

- Temel proje, belirli bir proje alt türüne ayrılmış bir XML parçasını geçirir veya alır ve bu mekanizmayı toplama düzeyleri arasındaki kalıcı durum olarak kullanır.

- Temel proje, bir GUID 'ye geçirme <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementation en dıştaki proje alt türünün ' i çağırır. GUID en dıştaki proje alt türüne aitse, çağrıyı işler. Aksi halde, bir iç proje alt türüne çağrı atar ve bu, GUID 'ye karşılık gelen proje alt türü bulunana kadar bu şekilde devam eder.

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