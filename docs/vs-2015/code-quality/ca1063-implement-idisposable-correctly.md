---
title: "CA1063: IDisposable 'ı doğru uygulayın | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1fe2982ab9e1b3951583b268eadb44c97c8e4805
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663630"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: IDisposable'ı doğru uygulayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 `IDisposable` doğru uygulanmadı. Bu sorunun bazı nedenleri aşağıda listelenmiştir:

- IDisposable, sınıfında yeniden uygulanır.

- Finalize yeniden geçersiz kılındı.

- Dispose geçersiz kılındı.

- Dispose () public, Sealed veya adlandırılmış Dispose değil.

- Dispose (bool) korumalı, sanal veya korumasız değil.

- Korumasız türlerde Dispose () Dispose (true) çağrılmalıdır.

- Korumasız türler için, Finalize, Dispose (bool) ya da Case sınıfı sonlandırıcısını çağırmaz.

  Bu desenlerden herhangi birinin ihlal olması bu uyarıyı tetikler.

  Her korumasız kök IDisposable türü kendi korumalı sanal void Dispose (bool) metodunu sağlamalıdır. Dispose () Dispose (true) öğesini çağırmalıdır ve Finalize, Dispose (false) çağrısını çağırmalıdır. Korumasız bir kök IDisposable türü oluşturuyorsanız Dispose (bool) tanımlamanız ve bunu çağırmanız gerekir. Daha fazla bilgi için, .NET Framework belgelerinin [çerçeve tasarım yönergeleri](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) bölümünde [yönetilmeyen kaynakları temizleme](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) bölümüne bakın.

## <a name="rule-description"></a>Kural Tanımı
 Tüm IDisposable türleri Dispose kalıbını doğru uygulamalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Kodunuzu inceleyin ve aşağıdaki çözümlerden hangisinin bu ihlalin düzelceğini saptayın.

- @No__t_0 tarafından uygulanan arabirimler listesinden IDisposable 'yi kaldırın ve bunun yerine temel sınıf Dispose uygulamasını geçersiz kılın.

- @No__t_0 türünden sonlandırıcıyı kaldırın, Dispose (bool disposing) öğesini geçersiz kılın ve sonlandırma mantığını ' disposing ' değeri false olan kod yoluna koyun.

- @No__t_0 kaldırın, Dispose (bool disposing) öğesini geçersiz kılın ve Dispose mantığını ' disposing ' değeri true olduğunda kod yoluna koyun.

- @No__t_0 public ve Sealed olarak bildirildiği için emin olun.

- @No__t_0 ' Dispose ' olarak yeniden adlandırın ve Public ve Sealed olarak belirtilen şekilde ayarlandığından emin olun.

- @No__t_0 korumalı, sanal ve korumasız olarak bildirildiği için emin olun.

- @No__t_0, Dispose (true) yöntemini çağıracak şekilde değiştirin ve ardından GC çağırır. Geçerli nesne örneğinde (' this ' veya ' Me ' [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) SuppressFinalize ve sonra döndürür.

- @No__t_0, Dispose (false) yöntemini çağıracak ve sonra geri döndüren şekilde değiştirin.

- Korumasız bir kök IDisposable sınıfı yazıyorsanız, IDisposable uygulamasının bu bölümde daha önce açıklanan modele uyduğundan emin olun.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="pseudo-code-example"></a>Sözde kod örneği
 Aşağıdaki sözde kod, Dispose (bool) ' ın yönetilen ve yerel kaynakları kullanan bir sınıfta nasıl uygulanması gerektiği hakkında genel bir örnek sağlar.

```
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

// Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }
    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources itself, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }
    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```
