---
title: 'CA2153: bozuk durum özel durumlarını Işlemeyi önleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 418cc9cb-68ad-47e9-a6c8-a48b9c35db45
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9d4ca2668f2d6241e9a3cca88b4722ee5348abc3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667417"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Bozuk Durum Özel Durumlarını İşlemekten Kaçının
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 [Bozuk durum özel durumları (CSE)](https://msdn.microsoft.com/magazine/dd419661.aspx) , işlemde belleğin bozulma olduğunu gösterir. Bir saldırgan bozuk bellek bölgesine bir yararlanma işlemi gerçekleştirilebileceği takdirde, işlemin çökmesine izin vermek yerine bunları yakalama güvenlik açıklarına yol açabilir.

## <a name="rule-description"></a>Kural Tanımı
 CSE, bir işlemin durumunun bozuk olduğunu ve sistem tarafından yakalanmadığını gösterir. Bozuk durum senaryosunda, bir genel işleyici yalnızca uygun `HandleProcessCorruptedStateExceptions` özniteliğiyle yönteminizin işaretlenmesi durumunda özel durumu yakalar. Varsayılan olarak, [ortak dil çalışma zamanı (CLR)](https://msdn.microsoft.com/library/8bs2ecf4.aspx) CSEs için catch işleyicilerini çağırmaz.

 İşlemin bu tür özel durumlar yakalanmadan kilitlenmesine izin vermek en güvenli seçenektir, hatta günlük kodu, saldırganların bellek bozulması hatalarından faydalara izin verebilir.

 Bu uyarı, catch (özel durum) veya catch (özel durum belirtimi yok) gibi tüm özel durumları yakalayan genel bir işleyici ile CSEs yakalama sırasında tetiklenir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu uyarıyı çözmek için aşağıdakilerden birini yapmalısınız:

 1. @No__t_0 özniteliğini kaldırın. Bu, CSEs 'nin catch işleyicilerine geçirilmediği varsayılan çalışma zamanı davranışına geri döner.

 2. Özel özel durum türlerini yakalayacak işleyicilerin tercih halinde genel catch işleyicisini kaldırın.  Bu, işleyici kodunun güvenli bir şekilde işleyebileceğini (çok nadir) kabul eden bir CSEs içerebilir.

 3. Özel durumun çağırana geçirilmesini sağlayan catch işleyicisinde CSE 'yi yeniden oluşturun ve çalışan işlemin sona ermesini sağlar.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="pseudo-code-example"></a>Sözde kod örneği

### <a name="violation"></a>Edildiği
 Aşağıdaki sözde kod, bu kural tarafından algılanan kalıbı gösterir.

```
[HandleProcessCorruptedStateExceptions]
//method to handle and log CSE exceptions
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
    }
}
```

### <a name="solution-1"></a>Çözüm 1
 HandleProcessCorruptedExceptions özniteliğini kaldırmak, özel durumların işlenmemesini sağlar.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-2"></a>Çözüm 2
 Genel catch işleyicisini kaldırın ve yalnızca belirli özel durum türlerini yakalayın.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle error
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle error
    }
}
```

### <a name="solution-3"></a>Çözüm 3
 Özel durumu yeniden oluşturun.

```
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle error
        throw;
    }
}
```
