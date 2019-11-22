---
title: Özellik sayfaları, JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffb1298981481bde063de898dc81c02dad548888
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297827"
---
# <a name="property-pages-javascript"></a>Özellik Sayfaları, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Özellik sayfaları**, proje ayarlarına erişim sağlar. Proje özelliklerini değiştirmek için **özellik sayfalarında** görünen sayfaları kullanabilirsiniz.

 Proje özelliklerine erişmek için **Çözüm Gezgini**bir proje düğümü seçin. **Proje** menüsünde **Özellikler**' e tıklayın.

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

 Aşağıdaki sayfalar ve Seçenekler **özellik sayfalarında**görünür.

## <a name="configuration-and-platform-page"></a>Yapılandırma ve platform sayfası
 Görüntülenecek veya değiştirilecek olan yapılandırmayı ve platformu seçmek için aşağıdaki seçenekleri kullanın.

 **Yapılandırma** Görüntülenecek veya değiştirilecek yapılandırma ayarlarını belirtir. Ayarlar **hata ayıklama** (varsayılan), **yayın**, **tüm yapılandırmalar**veya Kullanıcı tanımlı bir yapılandırmadır. Daha fazla bilgi için bkz. [hata ayıklama ve yayın projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Platform** Görüntülenecek veya değiştirilecek platform ayarlarını belirtir. Ayarlar **herhangi BIR CPU** ([!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] uygulamalar için varsayılan), **x64**, **ARM**, **x86**veya Kullanıcı tanımlı bir platform. Daha fazla bilgi için bkz. [hata ayıklama ve yayın projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="general-page"></a>Genel sayfa
 Projenin genel özelliklerini ayarlamak için aşağıdaki seçenekleri kullanın.

> [!NOTE]
> Bazı seçenekler yalnızca Windows Mağazası uygulamalarında kullanılabilir.

 **Çıkış yolu** Projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Yol görelidir; mutlak bir yol girerseniz, mutlak yol projeye kaydedilir. Varsayılan yol bin\Debug.

 Basitleştirilmiş derleme yapılandırması kullandığınızda, proje sistemi bir hata ayıklama veya yayın sürümü oluşturulup oluşturulmayacağını belirler. **Hata Ayıkla**, **hata ayıklamayı Başlat** (veya F5 tuşuna basın) ' e tıkladığınızda, belirttiğiniz **çıkış yolundan** bağımsız olarak derleme hata ayıklama konumuna konur. Ancak, **Yapı** menüsündeki **Build Solution** komutu onu belirttiğiniz konuma koyar. Gelişmiş derleme yapılandırmalarının etkinleştirilmesi için menü çubuğunda **Araçlar**, **Seçenekler**' i seçin. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin, **genel**' i seçin ve ardından **Gelişmiş derleme yapılandırmasını göster** onay kutusunu temizleyin. Bu, tüm yapılandırma değerleri üzerinde el ile denetim elde etmenizi ve bir hata ayıklama ya da sürüm sürümünün oluşturulup oluşturulmayacağını sağlar. Daha fazla bilgi için bkz. [nib: genel, projeler ve çözümler, Seçenekler Iletişim kutusu](https://msdn.microsoft.com/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).

 **Varsayılan dil** Proje için varsayılan dili belirtir. Denetim Masası 'nda **saat, dil ve bölge** ' de seçilen dil seçeneği kullanıcının tercih ettiği dili belirtir. Proje için varsayılan bir dil belirterek, kullanıcının tercih ettiği dilin uygulamada belirtilen dil kaynaklarıyla eşleşmemesi durumunda belirtilen varsayılan dil kaynaklarının kullanıldığından emin olursunuz.

## <a name="debug-page"></a>Hata ayıklama sayfası
 Projedeki hata ayıklama davranışının özelliklerini ayarlamak için aşağıdaki seçenekleri kullanın.

> [!NOTE]
> Bazı seçenekler yalnızca Windows Mağazası uygulamalarında kullanılabilir.

 **Başlatılacak hata ayıklayıcı** Hata ayıklayıcı için varsayılan Konağı belirtir.

- Uygulamayı Visual Studio konak bilgisayarında başlatmak için **yerel makine** ' yi seçin. Daha fazla bilgi için bkz. [Yerel makinede uygulamaları çalıştırma](https://go.microsoft.com/fwlink/?LinkId=234912).

- Simülatör 'da uygulamayı başlatmak için **simülatör** ' ı seçin. Daha fazla bilgi için bkz. [simülatörde uygulamaları çalıştırma](https://go.microsoft.com/fwlink/?LinkId=234913).

- Uzak bir bilgisayarda uygulamayı başlatmak için **uzak makine** ' yi seçin. Uzaktan hata ayıklama hakkında daha fazla bilgi için bkz. [uzak makinede uygulamaları çalıştırma](https://go.microsoft.com/fwlink/?LinkId=234914).

  **Uygulamayı Başlat** F5 tuşuna bastığınızda veya **Hata Ayıkla**, **hata ayıklamayı Başlat**' a tıkladığınızda uygulamanın başlatılıp başlatılmayacağını belirtir. Uygulamayı başlatmak için **Evet** ' i seçin; Aksi takdirde **Hayır**' ı seçin. **Hayır**' ı seçerseniz, uygulamayı başlatmak için farklı bir yöntem kullanıyorsanız uygulamada hata ayıklamaya devam edebilirsiniz.

  **Hata ayıklayıcı türü** Hata ayıklaması yapılacak kod türlerini belirtir. JavaScript kodunda hata ayıklamak için **yalnızca betiği** seçin. Yalnızca ortak dil çalışma zamanı tarafından yönetilen kodda hata ayıklama için **yönetilen** ' ı seçin. **Yalnızca** hata ayıklama C++ kodunda yerel ' i seçin. Hata ayıklama C++ ve JavaScript için **betiği ile yerel** ' i seçin. Hem yönetilen hem de C++ kodun hatalarını ayıklamak için **karışık (yönetilen ve yerel)** seçeneğini belirleyin.

  **Yerel ağ geri döngüsüne Izin ver** Uygulama testi için IP geri döngü adresine erişime izin verilip verilmeyeceğini belirtir. İstemci uygulaması, sunucu uygulamasının çalıştığı makinada ise geri döngü adresinin kullanılmasına izin vermek için **Evet** ' i seçin; Aksi takdirde **Hayır**' ı seçin. Bu özellik yalnızca, **başlatma Için hata ayıklayıcı** özelliği **uzak makine**olarak ayarlanırsa kullanılabilir.

  **Makine adı** Hata ayıklayıcıyı barındıracak uzak bilgisayarın adını belirtir. Bu özellik yalnızca **başlatma Için hata ayıklayıcı** **uzak makineye**ayarlanmışsa kullanılabilir.

  **Kimlik doğrulaması gerektir** Uzak bilgisayarın kimlik doğrulaması gerektirip gerektirmediğini belirtir. Bu özellik yalnızca **başlatma Için hata ayıklayıcı** **uzak makineye**ayarlanmışsa kullanılabilir.
