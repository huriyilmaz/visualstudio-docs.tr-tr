---
title: MSBuild Proje Dosyasında Kalıcı Veri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e83526007f676ae94ddce57936b627bcb4308c2a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706690"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>MSBuild Proje Dosyasında Verileri Kalıcı Hale Getirme
Proje alt türünün daha sonra kullanılmak üzere proje dosyasında alt sınıfa özgü verileri devam etmesi gerekebilir. Proje alt türü, aşağıdaki gereksinimleri karşılamak için proje dosyası kalıcılığını kullanır:

1. Projeyi oluşturmanın bir parçası olarak kullanılan verileri kalıcı olarak sataş. (Microsoft Build Engine hakkında daha fazla bilgi için BKZ. [MSBuild.)](../../msbuild/msbuild.md) Yapıyla ilgili bilgiler aşağıdakileri yapabilir:

    1. Yapılandırmadan bağımsız veriler. Diğer bir deyişle, boş veya eksik koşullarda MSBuild öğelerinde depolanan veriler.

    2. Yapılandırmaya bağlı veriler. Diğer bir deyişle, belirli bir proje yapılandırması için koşullandırılmış MSBuild öğelerinde depolanan veriler. Örnek:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Oluşturmakla ilgili olmayan verileri sür Bu veriler, bir XML şemasına karşı doğrulanmayan serbest biçimli XML ile ifade edilebilir.

    1. Yapılandırmadan bağımsız veriler.

    2. Yapılandırmaya bağlı veriler.

## <a name="persisting-build-related-information"></a>Kalıcı Yapı Yla İlgili Bilgiler
 Bir proje oluşturmak için yararlı verilerin kalıcılığı MSBuild üzerinden işlenir. MSBuild sistemi, yapıyla ilgili bilgilerin ana tablosunu tutar. Proje alt türleri, özellik değerlerini almak ve ayarlamak için bu verilere erişmekle yükümlüdür. Proje alt türleri, kalıcı olacak ek özellikler ekleyerek ve kalıcı olmayacak şekilde özellikleri kaldırarak yapıyla ilgili veri tablosunu da genişletebilir.

 MSBuild verilerini değiştirmek için, bir proje alt türü MSBuild özellik nesnesini temel proje <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>sisteminden . <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>çekirdek proje sistemi ve çalışan `QueryInterface`tarafından bunun için biraraya gelen proje alt türü sorguları uygulanan bir arayüzdür.

 Aşağıdaki yordam, bir özelliği kullanarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>kaldırmak için adımları özetliyor.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Bir özelliği MSBuild proje dosyasından kaldırmak için

1. Proje alt türünü arayın. `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>

2. Kaldırmak <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> `pszPropName` istediğiniz özelliği ayarlamak la arayın.

### <a name="persisting-non-build-related-information"></a>Kalıcı Yapı Dışı İlgili Bilgiler
 Oluşturmak için önemli olmayan proje dosyalarındaki verilerin kalıcılığı. <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>

 Ana `project subtype aggregator` nesneye, nesneye `project subtype project configuration` veya her ikisine de uygulayabilirsiniz. <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>

 Aşağıdaki noktalar, yapı dışı ilişkili bilgilerin kalıcılığıile ilgili temel kavramları özetler.

- Temel proje, yapılandırma bağımsız verileri yüklemek ve kaydetmek için ana proje alt türünü (yani en dıştaki proje alt türü) toplayıcı nesneyi çağırır ve yapılandırmaya bağımlı verileri yüklemek veya kaydetmek için proje alt türü proje yapılandırma nesnelerini çağırır.

- Temel proje, proje <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> alt türü toplamanın her düzeyi için birden çok kez yöntemleriçağırır ve her düzey için GUID'i geçer.

- Temel proje, belirli bir proje alt türüne adanmış bir XML parçasını geçer veya alır ve bu mekanizmayı toplama düzeyleri arasında kalıcı bir durum olarak kullanır.

- Temel proje, en dıştaki proje <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>alt tipinin uygulanmasını guid'de geçen olarak çağırır. GUID en dıştaki proje alt türüne aitse, çağrının kendisini işler; aksi takdirde, GUID'nin karşılık verdiği proje alt türü bulunana kadar çağrıyı bir iç proje alt türüne verir.

- Proje alt türü, XML parçasını çağrıyı iç proje alt türüne devretmeden önce veya sonra da değiştirebilir. Aşağıdaki örnek, proje alt türüne özgü özellikler içeren bir dosyanın adının bu proje alt türüne geçirildiği proje dosyasından bir alıntıyı gösterir.

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
