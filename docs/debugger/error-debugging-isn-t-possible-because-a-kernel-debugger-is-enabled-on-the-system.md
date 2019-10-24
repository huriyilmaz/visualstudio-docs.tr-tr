---
title: 'Hata: sistemde bir çekirdek&#39;hata ayıklayıcısı etkinleştirildiğinden dolayı hata ayıklama yapılamıyor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- kernel debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a966869ff1d200a51c6019a6ae937bea7c447bd
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737740"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Hata: sistemde bir çekirdek&#39;hata ayıklayıcısı etkinleştirildiğinden dolayı hata ayıklama yapılamıyor
Yönetilen kodda hata ayıklarken, aşağıdaki hata iletisini alabilirsiniz:

```cmd
Debugging isn't possible because a kernel debugger is enabled on the system
```

 Bu ileti, yönetilen kodda hata ayıklamaya çalıştığınızda oluşur:

- hata ayıklama modunda başlatılan bir [!INCLUDE[win7](../debugger/includes/win7_md.md)] veya [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)]system.

- uygulama CLR 2,0, 3,0 veya 3,5 CLR sürümünü kullanır.

## <a name="solution"></a>Çözüm

#### <a name="to-fix-this-problem"></a>Bu sorunu gidermek için

- Uygulamanızı CLR sürüm 4,0 veya 4,5 kullanmak üzere yükseltin

   —veya—

- @No__t_0 'de çekirdek hata ayıklamayı ve hata ayıklamayı devre dışı bırakın.

   —veya—

- @No__t_0 yerine çekirdek hata ayıklayıcısını kullanarak hata ayıklayın.

   —veya—

- Çekirdek hata ayıklayıcısında Kullanıcı modu özel durumlarını devre dışı bırakın.

#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Geçerli oturumda çekirdek hata ayıklamasını devre dışı bırakmak için

- Komut isteminde, şunları yazın:

    ```cmd
    Kdbgctrl.exe -d
    ```

#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Tüm oturumlarda çekirdek hata ayıklamayı devre dışı bırakmak için (Windows Vista ve Windows 7)

1. Komut isteminde, şunları yazın:

    ```cmd
    bcdedit /debug off
    ```

2. Bilgisayarı yeniden başlatın.

#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Tüm oturumlarda çekirdek hata ayıklamayı devre dışı bırakmak için (diğer Windows işletim sistemleri)

1. Sistem sürücünüzde Boot. ini dosyasını bulun (genellikle C: \\). Boot. ini dosyası gizli ve Salt okunabilir olabilir. Bu nedenle, görüntülemek için aşağıdaki komutu kullanmanız gerekir:

    ```cmd
    dir /ASH
    ```

2. Not defteri 'Ni kullanarak Boot. ini dosyasını açın ve aşağıdaki seçenekleri kaldırın:

    ```cmd
    /debug
    /debugport
    /baudrate
    ```

3. Bilgisayarı yeniden başlatın.

#### <a name="to-debug-with-the-kernel-debugger"></a>Çekirdek hata ayıklayıcı ile hata ayıklamak için

1. Çekirdek hata ayıklayıcı bağlanarsa, hata ayıklamaya devam etmek isteyip istemediğinizi soran bir ileti görürsünüz. Devam etmek için düğmeye tıklayın.

2. Bu durumda bir `User break exception(Int 3).` alabilirsiniz, hata ayıklamaya devam etmek için aşağıdaki çekirdek hata ayıklayıcı komutunu yazın:

     `gn`

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
