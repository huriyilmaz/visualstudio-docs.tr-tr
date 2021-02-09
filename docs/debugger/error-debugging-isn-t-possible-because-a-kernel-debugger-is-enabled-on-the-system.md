---
title: '&apos;Sistemde bir çekirdek hata ayıklayıcısı etkinleştirildiğinden dolayı hata ayıklama yapılamıyor | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a06ed9092145188bf5fbecd2caeb42f5ad5c2e3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871773"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Hata: sistemde bir çekirdek hata ayıklayıcısı etkinleştirildiğinden, ISN&#39;t hata ayıklaması mümkün
Yönetilen kodda hata ayıklarken, aşağıdaki hata iletisini alabilirsiniz:

```cmd
Debugging isn't possible because a kernel debugger is enabled on the system
```

 Bu ileti, yönetilen kodda hata ayıklamaya çalıştığınızda oluşur:

- [!INCLUDE[win7](../debugger/includes/win7_md.md)] [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] hata ayıklama modunda başlatılan bir veya sisteminde.

- uygulama CLR 2,0, 3,0 veya 3,5 CLR sürümünü kullanır.

## <a name="solution"></a>Çözüm

#### <a name="to-fix-this-problem"></a>Bu sorunu gidermek için

- Uygulamanızı CLR sürüm 4,0 veya 4,5 kullanmak üzere yükseltin

   —veya—

- İçinde çekirdek hata ayıklamayı ve hata ayıklamayı devre dışı bırakın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

   —veya—

- Yerine çekirdek hata ayıklayıcısını kullanarak hata ayıklayın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

   —veya—

- Çekirdek hata ayıklayıcısında Kullanıcı modu özel durumlarını devre dışı bırakın.

#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Geçerli oturumda çekirdek hata ayıklamasını devre dışı bırakmak için

- Komut istemine şunları yazın:

    ```cmd
    Kdbgctrl.exe -d
    ```

#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Tüm oturumlarda çekirdek hata ayıklamayı devre dışı bırakmak için (Windows Vista ve Windows 7)

1. Komut istemine şunları yazın:

    ```cmd
    bcdedit /debug off
    ```

2. Bilgisayarı yeniden başlatın.

#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Tüm oturumlarda çekirdek hata ayıklamayı devre dışı bırakmak için (diğer Windows işletim sistemleri)

1. Sistem sürücünüzde boot.ini bulun (genellikle C: \\ ). boot.ini dosyası gizli ve salt okunurdur. Bu nedenle, görüntülemek için aşağıdaki komutu kullanmanız gerekir:

    ```cmd
    dir /ASH
    ```

2. Not defteri 'Ni kullanarak boot.ini açın ve aşağıdaki seçenekleri kaldırın:

    ```cmd
    /debug
    /debugport
    /baudrate
    ```

3. Bilgisayarı yeniden başlatın.

#### <a name="to-debug-with-the-kernel-debugger"></a>Çekirdek hata ayıklayıcı ile hata ayıklamak için

1. Çekirdek hata ayıklayıcı bağlanarsa, hata ayıklamaya devam etmek isteyip istemediğinizi soran bir ileti görürsünüz. Devam etmek için düğmeye tıklayın.

2. `User break exception(Int 3).`Bu durum oluşursa, hata ayıklamaya devam etmek için aşağıdaki çekirdek hata ayıklayıcı komutunu yazın:

     `gn`

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
