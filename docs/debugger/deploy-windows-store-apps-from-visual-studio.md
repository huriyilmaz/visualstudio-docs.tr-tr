---
title: UWP uygulamalarını dağıtma | Microsoft Docs
ms.custom: seodec18
ms.date: 01/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: b2fa0bd62b88602ee5a4d5091821e2c2a18f6374
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430768"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Visual Studio’dan UWP uygulamaları dağıtma

Visual Studio dağıtım işlevselliği, bir hedef cihazda Visual Studio ile oluşturulan UWP uygulamalarını oluşturur ve kaydeder. Uygulamanın nasıl kaydedildiği, hedef cihazın yerel mi yoksa uzak mı olduğuna bağlıdır:

- Hedef, yerel Visual Studio makinesi olduğunda, Visual Studio uygulamayı Build klasöründen kaydeder.

- Hedef uzak bir cihaz olduğunda, Visual Studio gerekli dosyaları uzak makineye kopyalar ve uygulamayı bu cihaza kaydeder.

Uygulamanızı Visual Studio 'dan hata **ayıklamayı Başlat** seçeneğini (klavye: F5) veya **hata ayıklama olmadan Başlat** SEÇENEĞINI (klavye: CTRL + F5) kullanarak yaptığınızda dağıtım otomatik olarak yapılır. Uygulamanızı el ile de dağıtabilirsiniz. Aşağıdaki senaryolarda el ile dağıtım yararlı olur:

- Yerel veya uzak bir makinede geçici test.

- Hata ayıklamak istediğiniz başka bir uygulamayı başlatacak bir uygulama dağıtma.

- Başka bir uygulama veya yöntem tarafından başlatıldığında Ayıklanacak bir uygulama dağıtma.

## <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a>UWP uygulaması dağıtma
 Uygulamayı el ile dağıtmak basit bir işlemdir:

1. Uzak bir cihaza dağıtıyorsanız, uygulamanın başlangıç projesinin Özellik projesi sayfasında cihazın adını veya IP adresini belirtin. (Bunu yapmak için adımlar bu konuda daha sonra listelenmiştir.).

2. Hata ayıklayıcı Visual Studio araç çubuğunda, **hata ayıklamayı Başlat** düğmesinin yanındaki açılan listeden dağıtım hedefini seçin.

     ![Yerel makinede Çalıştır](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3. **Yapı** menüsünde **Dağıt** ' ı seçin.

## <a name="BKMK_How_to_specify_a_remote_device"></a>Uzak cihaz belirtme

**Önkoşullar**

Windows 10 uzak cihazda [Geliştirici modunu](/windows/uwp/get-started/enable-your-device-for-development)etkinleştirmeniz gerekir. Oluşturanın güncelleştirme veya sonrasını çalıştıran Windows 10 cihazlarında, uygulamanızı dağıtırken uzak Araçlar otomatik olarak yüklenir. Daha fazla bilgi için bkz. [yüklü uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md).

> [!NOTE]
> Windows 10 ' un ön oluşturanın güncelleştirme sürümlerinde, Visual Studio için Uzak Araçlar uzak cihaza yüklenmelidir ve uzaktan hata ayıklayıcı çalışıyor olmalıdır.

Dağıtım, uzak cihaza uygulama dosyalarını göndermek için uzaktan hata ayıklayıcı ağ kanalını kullanır.

#### <a name="to-specify-a-remote-device"></a>Uzak bir cihaz belirtmek için

1. Başlangıç projesinin hata ayıklama özelliği sayfasında, uzak dağıtım hedefinin adını veya IP adresini belirtin.

2. Hata ayıklama özelliği sayfasını açmak için Çözüm Gezgini ' de projeyi seçin ve sonra kısayol menüsünden **Özellikler** ' i seçin.

3. Sonra özellik sayfaları penceresinde **hata ayıklama** düğümünü seçin.

4. **Hedef cihaz**Için **uzak makine**' yi seçin.

5. **Uzak makine**altında **bul**' a tıklayın.

6. Uzak cihazın adını veya IP adresini yazabilir veya **uzak bağlantı** iletişim kutusundan cihazı seçebilirsiniz.

    ![Uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusu](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    **Uzak bağlantı** iletişim kutusu, yerel ağ alt ağındaki ve bir Ethernet kablosu tarafından doğrudan Visual Studio makinesine bağlı olan tüm cihazlardan cihazları görüntüler.

   **Uzak cihazı bir C++ proje sayfasında belirtme**

   ![Uzaktan&#43; &#43; hata ayıklama için C proje özellikleri](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. **Başlatma** listesinden **Uzaktan hata ayıklayıcı** ' yı seçin.

8. **Makine adı** kutusuna uzak cihazın ağ adını girin. İsterseniz, uzaktan hata ayıklayıcı bağlantısı Seç iletişim kutusundan cihazı seçmek için kutudaki aşağı oku seçebilirsiniz.

   **Uzak aygıtı bir görsel C# ve Visual Basic proje sayfasında belirtme**

   ![Uzaktan hata ayıklama için yönetilen proje özellikleri](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. **Hedef cihaz** listesinden **uzak makine** ' yi seçin.

10. Uzak cihazın ağ adını **uzak makine** kutusuna girin veya **bul** ' a tıklayarak **Uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusundan cihazı seçin.

## <a name="BKMK_Deployment_options"></a>Dağıtım seçenekleri

Başlangıç projesinin hata ayıklama özelliği sayfasında aşağıdaki dağıtım seçeneklerini belirleyebilirsiniz.

**Ağ geri döngüsüne izin ver**

Güvenlik nedenleriyle, standart biçimde yüklenen bir UWP veya [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] uygulamasının yüklü olduğu cihaza ağ çağrıları yapmasına izin verilmez. Varsayılan olarak, Visual Studio dağıtımı, dağıtılan uygulama için bu kuraldan bir istisna oluşturur. Bu istisna, iletişim yordamlarını tek bir makinede test etmenizi sağlar. Uygulamanızı [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)] ' a göndermeden önce, uygulamanızı muafiyet olmadan test etmelisiniz.

Uygulamadan ağ geri döngü muafiyetini kaldırmak için:

- C# Ve Visual Basic hata ayıklama özelliği sayfasında, **ağ geri döngüsüne izin ver** onay kutusunu temizleyin.

- C++ Hata ayıklama özelliği sayfasında, **ağ geri döngü değerini izin ver** ' i **Hayır**olarak ayarlayın.

**Başlatma, ancak başlatıldığında kodumdaki hata ayıkla (C# ve Visual Basic)/uygulamayı Başlat ()C++**

Dağıtımı, uygulama başlatıldığında otomatik olarak bir hata ayıklama oturumu başlatacak şekilde yapılandırmak için:

- C# Ve Visual Basic hata ayıklama özelliği sayfasında, **başlatılmayın ' i işaretleyin, ancak başlatma sırasında kodumdaki hata ayıklayın** onay kutusunu işaretleyin.

- C++ Hata ayıklama özelliği sayfasında, **Uygulamayı Başlat** değerini **Evet**olarak ayarlayın.

## <a name="see-also"></a>Ayrıca Bkz.

- [Gelişmiş uzak dağıtım seçenekleri](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Yüklü uygulama paketinin hatalarını ayıklama](../debugger/debug-installed-app-package.md)
- [Visual Studio’dan uygulamaları çalıştırma](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)
