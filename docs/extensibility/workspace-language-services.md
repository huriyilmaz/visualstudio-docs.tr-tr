---
title: Visual Studio 'da çalışma alanları ve dil Hizmetleri | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2893ae2bcd70ff317ba799fea6cfd2751c685731
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952718"
---
# <a name="workspaces-and-language-services"></a>Çalışma alanları ve dil Hizmetleri

Dil Hizmetleri, çözüm ve projelerle çalışırken kullandıkları aynı zengin dil özelliklerine sahip kullanıcılar için [açık klasör](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) sağlayabilir. Bir dil hizmeti, açık bir belgenin dosya uzantısına veya içeriğine göre kendi kendini etkinleştirebilir ve bu "gevşek dosya" dil hizmeti söz dizimi vurgulaması ile sınırlıdır. Kaynak kodu düzenlenirken/gözden geçirirken daha zengin bir deneyim sağlamak için ek bilgiler gereklidir. Her dil hizmetinin, bir belge için bu ekstra bağlamsal verilerle başlatmak üzere kendi API 'SI vardır. Bu genellikle hem dil hizmetine hem de yapı sistemine sıkı bir şekilde bağlanmış bir proje sistemi tarafından yönetilir.

## <a name="initialization"></a>Başlatma

Bir [çalışma alanında](workspaces.md)dil Hizmetleri, <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> yalnızca söz konusu dil hizmetinde uzmanlaşmış ve derleme yazma bir şeyi bilen bir uzantı noktasıyla başlatılır. Bu şekilde, bir dil hizmeti sahibi bir derleme sırasında derleyicisini çalıştırmaya yönelik klasörler ve dosyalar içinde kaç desen var olursa olsun, tek bir açık klasör uzantısını koruyabilir (örneğin, MSBuild, makefiles, vb.). Dosya bağlamının oluşturulduğu dosyalar diskte değiştirildiğinde ve dosya bağlamı yenilendiğinde, dil hizmeti sağlayıcısına güncelleştirilmiş dosya bağlamları kümesi bildirilir. Dil hizmeti sağlayıcısı daha sonra modelini güncelleştirebilir.

Bir belge düzenleyicide açıldığında, Visual Studio yalnızca eşleşen dosya bağlamı sağlayıcısı bulunan dosya bağlamı türleri gerektiren dil hizmeti sağlayıcılarını kabul eder. Ardından, eşleşen sağlayıcılardan dosya bağlamını, ile seçilen dil hizmeti sağlayıcısına geçirir `ILanguageServiceProvider.InitializeAsync` . Bu dosya bağlamı verileriyle hangi dil hizmeti sağlayıcısının yaptığı, dil hizmeti sağlayıcısının uygulama ayrıntısı, ancak beklenen Kullanıcı deneyimi, bu açık belge için daha zengin bir dil hizmetidir.

## <a name="using-ilanguageserviceprovider"></a>Ilanguageserviceprovider kullanma

Dil `ContextType` `SupportedContextTypes` sunucusu dışarı aktarma özniteliği değerlerinden biriyle eşleşen bir dosya bağlamı oluşturulduğunda dil hizmetine bildirim gönderilir.

Bir dil hizmetini desteklemek için bir uzantıya şunlar gerekir:

- Benzersiz bir `Guid` . Bu, `SupportedContextTypes` öznitelik bağımsız değişkenleri ve bir nesnesi için kullanılacaktır `FileContext` .
- Dil dosyası bağlamı
  - Sağlayıcı fabrikası
    - `ExportFileContextProviderAttribute``Guid`üzerinde benzersiz olarak oluşturulan öznitelik`SupportedContextTypes`
    - Uygular `IWorkspaceProviderFactory<IFileContextProvider>`
  - Sağlayıcı uygulama `IFileContextProvider.GetContextsForFileAsync`
    - `FileContext` `contextType` Oluşturucu bağımsız değişkeniyle benzersiz olarak oluşturulan yeni bir oluşturun`Guid`
    - ' A `Context` `FileContext` ek veri vermek için özelliğini kullanın. `ILanguageServiceProvider`
- Dil hizmeti
  - Sağlayıcı fabrikası
    - `ExportLanguageServiceProvider``Guid`üzerinde benzersiz olarak oluşturulan öznitelik`SupportedContextTypes`
    - Uygular `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Sağlayıcı
    - Uygular `ILanguageServiceProvider`
    - `ILanguageServiceProvider.InitializeAsync`Dosya açıldığında belirtilen bağımsız değişkenler için dil hizmetlerini etkinleştirmek üzere kullanın
    - `ILanguageServiceProvider.UninitializeAsync`Dosya kapatıldığında belirtilen bağımsız değişkenler için dil hizmetlerini devre dışı bırakmak için kullanın

>[!WARNING]
>`ILanguageServiceProvider`Yöntemler, ana iş parçacığında çalışma alanı tarafından çağrılabilir. UI gecikmelerinden kaçınmak için farklı bir iş parçacığında iş zamanlamayı düşünün.

## <a name="language-server-protocol"></a>Dil Sunucusu Protokolü

`Microsoft.VisualStudio.Workspace.*`API 'ler, dil hizmetinizi açık klasörde etkinleştirmenin tek yolu değildir. Başka bir seçenek de dil sunucusu kullanmaktır. Daha fazla bilgi için [dil sunucusu protokolü](language-server-protocol.md)hakkında makalesini okuyun.

## <a name="related-interfaces"></a>İlgili arabirimler

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> , eşleşen dosya türlerindeki bir dosya açıldığında veya düzenlenmek üzere kapatıldığında çağrılır.

## <a name="next-steps"></a>Sonraki adımlar

* [Çalışma alanı derlemesi](workspace-build.md) -aç klasörü MSBuild ve makefiles gibi derleme sistemlerini destekler.