---
title: Visual Studio |'daki çalışma alanları ve dil hizmetleri Microsoft Docs
description: Dil hizmetlerinin Açık Klasör kullanıcılarına çözüm ve projelerle çalışırken kullanılan zengin dil özelliklerinin aynısını nasıl sağlay olduklarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 815cfb9e17fed38b519719010acd997f7fdc5242
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724945"
---
# <a name="workspaces-and-language-services"></a>Çalışma alanları ve dil hizmetleri

Dil hizmetleri, [Açık Klasör kullanıcılarına](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) çözüm ve projelerle çalışırken kullanılan zengin dil özelliklerinin aynısını sağlar. Bu "gevşek dosya" dil hizmeti söz dizimi vurgulama ile sınırlı olsa da dil hizmeti, dosya uzantısına veya açık bir belgenin içeriğine bağlı olarak kendi kendine etkinleştirebilirsiniz. Kaynak kodu düzenlerken/gözden geçirerek daha zengin bir deneyim sağlamak için ek bilgiler gereklidir. Her dil hizmetinin, bir belgeye ait bu ek bağlamsal verilerle başlatma için kendi API'si vardır. Bu genellikle hem dil hizmetine hem de derleme sistemine sıkı bir şekilde bağlı olan bir proje sistemi tarafından yönetilir.

## <a name="initialization"></a>Başlatma

Çalışma [alanında](workspaces.md)dil hizmetleri, yalnızca bu dil hizmetine özel olan ve derleme yazma hakkında hiçbir bilgi sahibi olan <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> bir uzantı noktası tarafından başlatılır. Bu şekilde dil hizmeti sahibi, derleme sırasında derleyicisini çalıştırmaya (örneğin, derleme dosyaları, derleme dosyaları vb.) ilişkin klasör ve dosya sayısına bakılmaksızın tek bir MSBuild Açık Klasör uzantısını sürdürebilir. Diskte bir dosya bağlamının oluşturularak oluşturulan dosyalar yenilendiğinde ve dosya bağlamı yenilendiğinde, dil hizmet sağlayıcısına güncelleştirilmiş dosya bağlamları kümesi bildirilecek. Dil hizmeti sağlayıcısı daha sonra modelini güncelleştirebilirsiniz.

Düzenleyicide bir belge açıldığında, Visual Studio yalnızca eşleşen bir dosya bağlamı sağlayıcısının buluna bir dosya bağlamı türü gerektiren dil hizmeti sağlayıcılarını göz önünde bulundurabilirsiniz. Ardından, eşleşen sağlayıcılardan dosya bağlamlarını aracılığıyla seçilen dil hizmet sağlayıcısına `ILanguageServiceProvider.InitializeAsync` iletir. Dil hizmeti sağlayıcısının bu dosya bağlamı verileriyle yaptığı, dil hizmeti sağlayıcısının uygulama ayrıntılarıdır, ancak beklenen kullanıcı deneyimi, açılan belge için daha zengin bir dil hizmetidir.

## <a name="using-ilanguageserviceprovider"></a>ILanguageServiceProvider Kullanma

Dil sunucusu dışarı aktarma özniteliğinin değerlerinden biri ile eşleşen bir dosya bağlamı `ContextType` `SupportedContextTypes` oluşturulduğunda dil hizmetine bildirilecek.

Dil hizmetini desteklemek için bir uzantıya şu gerekir:

- Benzersiz bir `Guid` . Bu, öznitelik bağımsız `SupportedContextTypes` değişkenleri ve bir nesnesinde `FileContext` kullanılır.
- Dil dosyası bağlamı
  - Sağlayıcı fabrikası
    - `ExportFileContextProviderAttribute` özniteliği ile yukarıdaki benzersiz olarak `Guid` oluşturulur `SupportedContextTypes`
    - Uygulayan `IWorkspaceProviderFactory<IFileContextProvider>`
  - Sağlayıcı uygulaması `IFileContextProvider.GetContextsForFileAsync`
    - Benzersiz olarak `FileContext` oluşturulan oluşturucu bağımsız `contextType` değişkeniyle yeni bir oluşturun `Guid`
    - ek `Context` veri vermek `FileContext` için özelliğini kullanın `ILanguageServiceProvider`
- Dil hizmeti
  - Sağlayıcı fabrikası
    - `ExportLanguageServiceProvider` özniteliği ile yukarıdaki benzersiz olarak `Guid` oluşturulur `SupportedContextTypes`
    - Uygulayan `IWorkspaceProviderFactory<ILanguageServiceProvider>`
  - Sağlayıcı
    - Uygulayan `ILanguageServiceProvider`
    - Bir `ILanguageServiceProvider.InitializeAsync` dosya açıldığında sağlanan bağımsız değişkenler için dil hizmetlerini etkinleştirmek için kullanın
    - Bir `ILanguageServiceProvider.UninitializeAsync` dosya kapatılan bağımsız değişkenler için dil hizmetlerini devre dışı bırakmak için kullanın

>[!WARNING]
>Yöntemler `ILanguageServiceProvider` ana iş parçacığında çalışma alanı tarafından çağrılabilir. Kullanıcı arabirimi gecikmelerini önlemek için işi farklı bir iş parçacığında zamanlamayı göz önünde bulundurabilirsiniz.

## <a name="language-server-protocol"></a>Dil Sunucusu Protokolü

Klasör `Microsoft.VisualStudio.Workspace.*` Aç'ta dil hizmetinizi etkinleştirmenin tek yolu API'ler değildir. Bir diğer seçenek de dil sunucusu kullanmaktır. Daha fazla bilgi için Dil Sunucusu Protokolü [hakkında bilgi okuyun.](language-server-protocol.md)

## <a name="related-interfaces"></a>İlgili arabirimler

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> eşleşen dosya türlerine sahip bir dosya düzenlemek için açıldığında veya kapatıldığında çağrılır.

## <a name="next-steps"></a>Sonraki adımlar

* [Çalışma alanı derlemesi](workspace-build.md) - Klasör Aç, çalışma alanı ve derleme MSBuild derleme sistemlerini destekler.