---
title: ASP.NET özel durumları için hata ayıklama | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: a6808bff0a38b6ebaa3049f1655e781439f3f735
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350140"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Nasıl Yapılır: ASP.NET Özel Durumlarında Hata Ayıklama
Hata ayıklama özel durumları, güçlü bir uygulama geliştirmesinin önemli bir parçasıdır [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] . Özel durumların hata ayıklamasına ilişkin genel bilgiler [hata ayıklayıcı Ile özel durumları yönetmektir](../debugger/managing-exceptions-with-the-debugger.md).

 İşlenmemiş özel durumların hatalarını ayıklamak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , hata ayıklayıcının onlar için durdurduğundan emin olmanız gerekir. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Çalışma zamanının en üst düzey bir özel durum işleyicisi vardır. Bu nedenle, hata ayıklayıcı varsayılan olarak işlenmemiş özel durumları hiçbir şekilde koparmazlar. Bir özel durum oluştuğunda hata ayıklayıcıya bölmek için, özel **durumlar** iletişim kutusunda özel durum ayarı için **bir özel** durum olduğunda kes ' i seçmeniz gerekir.

 Yalnızca kendi kodum etkinleştirdiyseniz, **bir özel durum oluştuğunda kes:** bir .net yönteminde veya diğer sistem kodunda bir özel durum oluşturulursa hata ayıklayıcının hemen kesilmesine neden olmaz. Bunun yerine, yürütme hata ayıklayıcı sistem dışı koda isabetyana kadar devam eder ve ardından kesilir. Sonuç olarak, bir özel durum oluştuğunda sistem kodunda ilerlemeyin.

 Yalnızca kendi kodum, size daha fazla yararlı olabilecek başka bir seçenek sunar: **bir özel durum olduğunda kes: Kullanıcı tarafından işlenmemiş**. Bir özel durum için bu ayarı seçerseniz, hata ayıklayıcı Kullanıcı kodundaki yürütmeyi keser, ancak özel durum, Kullanıcı kodu tarafından yakalanmaz ve işlenir. Bu ayar [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , bu işleyici Kullanıcı dışı kodda olduğundan, en üst düzey özel durum işleyicisinin etkisini geçersiz kılar.

### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Yalnızca kendi kodum ASP.NET özel durumların hata ayıklamasını etkinleştirmek için

1. **Hata Ayıkla** menüsünde **özel durumlar**' a tıklayın.

     **Özel durumlar** iletişim kutusu görüntülenir.

2. **Ortak dil çalışma zamanı özel durumları** satırında, **oluşturulan** veya **Kullanıcı tarafından işlenmeyen**' ı seçin.

     **Kullanıcı tarafından işlenmeyen** ayarı kullanmak için **yalnızca kendi kodum** etkinleştirilmelidir.

### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>ASP.NET özel durum işleme için en iyi yöntemleri kullanma

- `try ... catch`Kod etrafına blokları, tahmin ettiğiniz ve nasıl işleneceğini bildiğiniz özel durumlar oluşturabilecek şekilde yerleştirin. Örneğin, uygulama bir XML Web hizmetine ya da doğrudan bir SQL Server çağrılar yapıyor, bu kod TRY içinde olmalıdır **... **oluşabilecek çok sayıda özel durum olduğundan catch blokları.

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)