---
title: JıT Iyileştirme ve hata ayıklama | Microsoft Docs
description: İyileştirilmiş kod, hata ayıklama için olmayan koddan daha zordur. JıT iyileştirmesi ve ne zaman ve nasıl bastırılamıyor hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: be8a0b57bc009d776f20ca2bebae94627f4a4909
ms.sourcegitcommit: 7d319435c35075d4cec021b7b667666a81c02435
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137650282"
---
# <a name="jit-optimization-and-debugging"></a>JIT İyileştirmesi ve Hata Ayıklaması
Kodda hata ayıklamaya çalışıyorsanız, bu kod en iyi duruma **getirilmeyen** daha kolay olur. Kod iyileştirildiğinde, derleyici ve çalışma zamanı, daha hızlı çalışacak, ancak özgün kaynak koda daha az bir doğrudan eşlemeye sahip olacak şekilde, verilmiş CPU kodunda değişiklikler yapar. Eşleme daha az doğrudan ise, hata ayıklayıcılar genellikle yerel değişkenlerin değerini söyleyebilir ve kod Adımlama ve kesme noktaları beklemiş gibi çalışmayabilir.

> [!NOTE]
> JıT (tam zamanında) hata ayıklama hakkında daha fazla bilgi için [Bu belgeleri](../debugger/debug-using-the-just-in-time-debugger.md)okuyun.

## <a name="how-optimizations-work-in-net"></a>İyileştirmeler .NET 'te nasıl çalışır? 
Normalde yayın derleme yapılandırması iyileştirilmiş kod oluşturuyor ve hata ayıklama derleme yapılandırması değil. `Optimize`MSBuild özelliği, derleyicinin kodu iyileştirip söyetkinleştirilmeyeceğini denetler.

.NET ekosisteminde, kod iki adımlı bir işlemde kaynaktan CPU yönergelerine açıktır: ilk olarak, C# derleyicisi yazdığınız metni MSIL adlı bir ara ikili biçime dönüştürür ve MSIL 'i .dll dosyalara yazar. Daha sonra, .NET çalışma zamanı bu MSIL 'yi CPU yönergelerine dönüştürür. Her iki adım da bir ölçüde iyileştirebilirler, ancak .NET çalışma zamanı tarafından gerçekleştirilen ikinci adım daha önemli iyileştirmeleri gerçekleştirir.

## <a name="the-suppress-jit-optimization-on-module-load-managed-only-option"></a>' Modül yüklemesinde JıT iyileştirmesini bastır (yalnızca yönetilen) ' seçeneği
Hata ayıklayıcı, hedef işlemin içinde iyileştirmeler etkinken derlenen bir DLL yüklendiğinde ne olacağını denetleyen bir seçenek sunar. Bu seçenek işaretli değilse (varsayılan durum), .NET çalışma zamanı MSIL kodunu CPU koduna derlediğinde, iyileştirmeler etkin kalır. Seçenek işaretliyse, hata ayıklayıcı iyileştirmelerin devre dışı bırakıldığını ister.

**Modül yüklemesinde JIT iyileştirmesini gösterme (yalnızca yönetilen)** seçeneğini bulmak için **Araçlar**  >  **Seçenekler**' i seçin ve ardından **hata ayıklama** düğümünün altındaki **genel** sayfasını seçin.

![JıT Iyileştirmesini bastır](../debugger/media/suppress-jit-tool-options.png "JıT Iyileştirmesini bastır")

## <a name="when-should-you-check-the-suppress-jit-optimization-option"></a>' JıT iyileştirmesini bastır ' seçeneğini ne zaman denetlemeniz gerekir?
Bu seçeneği, bir NuGet paketi gibi başka bir kaynaktan dll 'Leri karşıdan yüklerken ve bu DLL 'deki kodda hata ayıklamak istediğinizde işaretleyin. Gizlemenin çalışması için bu DLL için simge (. pdb) dosyasını da bulmanız gerekir.

Yalnızca yerel olarak oluşturmakta olduğunuz kodun hatalarını ayıklamakla ilgileniyorsanız, bazı durumlarda bu seçeneğin etkinleştirilmesi, hata ayıklamanın önemli ölçüde yavaşlamasına neden olur. Bu yavaşlamaya yönelik iki neden vardır:

* İyileştirilmiş kod daha hızlı çalışır. Birçok kod için iyileştirmeleri devre dışı bırakırsanız, performans etkisi eklenebilir.
* Yalnızca kendi kodum etkinse, hata ayıklayıcı, iyileştirilmiş dll 'Ler için sembolleri yüklemeye da çalışır. Sembolleri bulma uzun zaman alabilir.

## <a name="limitations-of-the-suppress-jit-optimization-option"></a>' JıT iyileştirmesini bastır ' seçeneğinin sınırlamaları 
Bu seçeneği **açmak, bu** iki durum vardır:

1. Hata ayıklayıcıyı zaten çalışan bir işleme iliştirmekte olduğunuz durumlarda, bu seçeneğin hata ayıklayıcı eklendiği sırada zaten yüklenmiş modüller üzerinde hiçbir etkisi olmayacaktır.
2. Bu seçeneğin yerel koda önceden derlenmiş (a. k. a NGen) dll 'Leri üzerinde hiçbir etkisi yoktur. Ancak, **' COMPlus_ReadyToRun '** ortam değişkeniyle **' 0 '** olarak ayarlanmış işlemi başlatarak önceden derlenmiş kod kullanımını devre dışı bırakabilirsiniz. Bu, .NET Core çalışma zamanına önceden derlenmiş görüntülerin kullanımını devre dışı bırakarak çalışma zamanını JıT derleme çerçevesi koduna zorluyor. 

   .NET Framework hedefliyorsanız, **' COMPlus_ZapDisable '** ortam değişkenini ekleyin ve **' 1 '** olarak ayarlayın. 
   
`"COMPlus_ReadyToRun": "0"` *Properties\launchSettings.JSON* dosyasındaki her bir profile ekleyerek ayarlayın:

```json
{
  "iisSettings": {
    "windowsAuthentication": false,
    "anonymousAuthentication": true,
    "iisExpress": {
      "applicationUrl": "http://localhost:59694/",
      "sslPort": 44320
    }
  },
  "profiles": {
    "IIS Express": {
      "commandName": "IISExpress",
      "launchBrowser": true,
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development",
        "COMPlus_ReadyToRun": "0"
      }
    },
    "HttpLoggingSample": {
      "commandName": "Project",
      "launchBrowser": true,
      "environmentVariables": {
        "ASPNETCORE_ENVIRONMENT": "Development",
        "COMPlus_ReadyToRun": "0"
      },
      "applicationUrl": "https://localhost:5001;http://localhost:5000"
    }
  }
}
```


## <a name="see-also"></a>Ayrıca bkz.
- [DotNet Framework kaynağında hata ayıklama](../debugger/how-to-debug-dotnet-framework-source.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [Hata Ayıklayıcısı ile Kodlarda gezinme](../debugger/navigating-through-code-with-the-debugger.md)
- [Çalıştırma İşlemine İliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Yönetilen yürütme Işlemi](/dotnet/standard/managed-execution-process)
