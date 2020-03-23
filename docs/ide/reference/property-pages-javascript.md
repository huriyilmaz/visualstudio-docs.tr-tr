---
title: Özellik Sayfaları, JavaScript
ms.date: 06/21/2017
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6883e556cd70adddd45fd442d338e10d1cafa1e2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68926192"
---
# <a name="property-pages-javascript"></a>Özellik sayfaları, JavaScript

**Özellik Sayfaları** proje ayarlarına erişim sağlar. Proje özelliklerini değiştirmek için **Özellik Sayfalarında** görünen sayfaları kullanabilirsiniz.

Proje özelliklerine erişmek için **Çözüm Gezgini'nde**bir proje düğümü seçin. **Proje** menüsünde **Özellikler'i**tıklatın.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Aşağıdaki sayfalar ve seçenekler **Özellik Sayfalarında**görünür.

## <a name="configuration-and-platform-page"></a>Yapılandırma ve Platform Sayfası

Görüntülemek veya değiştirmek için yapılandırmayı ve platformu seçmek için aşağıdaki seçenekleri kullanın.

 **Yapılandırma**

Görüntülemek veya değiştirmek için yapılandırma ayarlarını belirtir. Ayarlar **Hata Ayıklama** (varsayılan), **Sürüm,** **Tüm Yapılandırmalar**veya kullanıcı tanımlı yapılandırmadır. Daha fazla bilgi için [bkz: Visual Studio'da hata ayıklama ve sürüm yapılandırmalarını ayarlayın.](../../debugger/how-to-set-debug-and-release-configurations.md)

 **Platform**

Görüntülenecek veya değiştirilen platform ayarlarını belirtir. Ayarlar **Herhangi bir CPU** [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] (uygulamalar için varsayılan), **x64**, **ARM**, **x86**veya kullanıcı tanımlı bir platform vardır. Daha fazla bilgi için [bkz: Visual Studio'da hata ayıklama ve sürüm yapılandırmalarını ayarlayın.](../../debugger/how-to-set-debug-and-release-configurations.md)

## <a name="general-page"></a>Genel Sayfa

Projenin genel özelliklerini ayarlamak için aşağıdaki seçenekleri kullanın.

> [!NOTE]
> Bazı seçenekler yalnızca UWP uygulamalarında kullanılabilir.

 **Çıkış Yolu**

Projenin yapılandırması için çıktı dosyalarının konumunu belirtir. Yol görecelidir; mutlak bir yol girerseniz, mutlak yol projede kaydedilir. Varsayılan yol bin\Debug'dur.

Basitleştirilmiş yapı yapılandırmaları kullandığınızda, proje sistemi hata ayıklama mı yoksa sürüm sürümü mü oluşturup oluşturmayacağını belirler. **Hata Ayıklama** > **Başlat Hata Ayıklama'yı** tıklattığınızda (veya **F5**tuşuna bastığınızda), yapı belirttiğiniz **Çıktı yolundan** bağımsız olarak hata ayıklama konumuna konur. Ancak, Yapı menüsündeki **Çözüm** **Oluştur** komutu, bu komutu belirttiğiniz konuma koyar. Gelişmiş yapı yapılandırmalarını etkinleştirmek için menü çubuğunda **Araç** > **Seçenekleri'ni**seçin. **Seçenekler** iletişim **kutusunda, Projeler ve Çözümler'i**genişletin, **Genel'i**seçin ve gelişmiş **yapı yapılandırmalarını göster** onay kutusunu temizleyin. Bu, tüm yapılandırma değerleri ve hata ayıklama veya sürüm sürümü oluşturulup oluşturulmadığı üzerinde el ile denetim sağlar.

 **Varsayılan Dil**

Projenin varsayılan dilini belirtir. Denetim Masası'nda **Saat, Dil ve Bölge'de** seçilen dil seçeneği, kullanıcının tercih ettiği dili belirtir. Proje için varsayılan bir dil belirterek, kullanıcının tercih ettiği dil uygulamada sağlanan dil kaynaklarıyla eşleşmiyorsa, belirtilen varsayılan dil kaynaklarının kullanıldığından emin olabilirsiniz.

## <a name="debug-page"></a>Hata Ayıklama Sayfası

Projedeki hata ayıklama davranışı için özellikleri ayarlamak için aşağıdaki seçenekleri kullanın.

> [!NOTE]
> Bazı seçenekler yalnızca UWP uygulamalarında kullanılabilir.

 **Debugger Başlatacak**

Hata ayıklama için varsayılan ana bilgisayarı belirtir.

- Visual Studio ana bilgisayarda uygulamayı başlatmak için **Yerel Makine'yi** seçin. Daha fazla bilgi için [bkz.](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

- Simülatörde uygulamayı başlatmak için **Simülatör'u** seçin. Daha fazla bilgi için [simülatördeki Uygulamaları Çalıştırma'ya](../../debugger/run-windows-store-apps-in-the-simulator.md)bakın.

- Uygulamayı uzak bir bilgisayarda başlatmak için **Uzak Makine'yi** seçin. Uzaktan hata ayıklama hakkında daha fazla bilgi için, [uzak bir makinede çalışan uygulamalar](../../debugger/run-windows-store-apps-on-a-remote-machine.md)abakın.

**Başlatma Uygulaması**

**F5** tuşuna bastığınızda uygulamayı başlatıp başlatmayacağınızı veya **Hata** > **Ayıklama Başlatma'yı**tıklattığınızda uygulamayı başlatıp başlatmayacağınızı belirtir. Uygulamayı başlatmak için **Evet'i** seçin; aksi takdirde, **Hayır'ı**seçin. **Hayır'ı**seçerseniz, başlatmak için farklı bir yöntem kullanırsanız uygulamayı yine de hata ayıklayabilirsiniz.

**Hata Ayıklama Türü**

Hata ayıklamak için kod türlerini belirtir. Yalnızca JavaScript kodunu hata ayıklamak için **Komut Dosyası'nı** seçin. Ortak dil çalışma zamanı tarafından yönetilen Yalnızca Hata Ayıklamak için **Yönetilen'i** seçin. C++ kodunu hata ayıklamak için **Yalnızca Yerel** Olarak'ı seçin. C++ ve JavaScript hata ayıklamak için **Script ile Yerel'i** seçin. Hem yönetilen hem de C++ kodunu hata ayıklamak için **Karışık (Yönetilen ve Yerel)** seçeneğini belirleyin.

**Yerel Ağ Loopback'e Izin Ver**

IP geri dönüş adresine erişimin uygulama testi için izin verilip verilmediğini belirtir. İstemci uygulaması sunucu uygulamasının çalıştığı aynı makinedeyse, geri dönüş adresinin kullanımına izin vermek için **Evet'i** seçin; aksi takdirde, **Hayır'ı**seçin. Bu özellik yalnızca **Başlat'ın Hata Ayıklama** özelliği **Uzak Makine**olarak ayarlanırsa kullanılabilir.

**Makine Adı**

Hata ayıklamayı barındırmak için uzak bilgisayarın adını belirtir. Bu özellik yalnızca **Başlatılan Hata Ayıklama** Uzak **Makine**olarak ayarlanırsa kullanılabilir.

**Kimlik Doğrulama Gerektirir**

Uzak bilgisayarın kimlik doğrulaması gerektiregörüp gerektirmediğini belirtir. Bu özellik yalnızca **Başlatılan Hata Ayıklama** Uzak **Makine**olarak ayarlanırsa kullanılabilir.
