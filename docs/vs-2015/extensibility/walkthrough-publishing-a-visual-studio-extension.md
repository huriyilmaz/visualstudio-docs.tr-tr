---
title: Uzantı yayımlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5238274d66296a21e15b47d1a090ab01c1a1299d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201977"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>İzlenecek Yol: Visual Studio Uzantısı Yayımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Note**: Visual Studio Galerisi Visual Studio Market değiştiriliyor. Ayrıntılar için bu konunun en son sürümüne bakın.

Bu izlenecek yol, Visual Studio uzantısının Visual Studio Galerisine nasıl yayımlanacağını göstermektedir. Uzantınızı galeriye eklediğinizde, geliştiriciler **uzantıları ve güncelleştirmeleri** kullanarak yeni ve güncelleştirilmiş uzantılara gözatabilirler.

## <a name="prerequisites"></a>Ön koşullar
 Bu yönergeyi izlemek için, Visual Studio SDK 'sını yüklemelisiniz. Daha fazla bilgi için bkz. [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Visual Studio uzantısı oluşturma
 Bu durumda, varsayılan VSPackage uzantısını kullanacağız, ancak aynı adımlar her uzantı türü için geçerli olur.

1. Bir menü komutu olan adlı C# adlı bir VSPackage oluşturun `TestPublishing` . Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="test-the-extension"></a>Uzantıyı test etme
 Uzantıyı dağıtmadan önce, Visual Studio 'nun deneysel örneğine doğru yüklendiğinden emin olmak için oluşturun ve test edin.

1. Visual Studio 'da hata ayıklamayı başlatın. Visual Studio 'nun deneysel bir örneğini açmak için.

2. Deneysel örnekte, **Araçlar** menüsüne gidin ve **Uzantı Yöneticisi**' ne tıklayın. TestPublishing uzantısı, Orta bölmede görünmelidir ve etkinleştirilmelidir.

3. **Araçlar** menüsünde, test komutunu görtığınızdan emin olun.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Uzantıyı Visual Studio Galerisine yayımlayın
 Artık uzantıyı Visual Studio Galerisi ' ne yayımlayabilirsiniz.

1. Uzantınızın yayın sürümünü derlediğinizden ve güncel olduğundan emin olun.

2. Bir Web tarayıcısında [Visual Studio Market](https://marketplace.visualstudio.com/) Web sitesini açın.

3. Sağ üst köşede **oturum aç**' a tıklayın.

4. Oturum açmak için Microsoft hesabı kullanın. Bir Microsoft hesabı yoksa, bu noktada bir tane oluşturabilirsiniz.

5. **Karşıya Yükle**'ye tıklayın.

6. **Adım 1: uzantı türü**' nde **araç** ' i seçin ve ardından **İleri**' ye tıklayın.

7. **2. Adım: karşıya yükleme**' de, doğrudan Visual Studio Galerisine yüklemeyi seçebilir veya yalnızca kendi web sitenizin bağlantısını ekleyebilirsiniz. Bu durumda, **aracımı karşıya yüklemek istiyorum**' u seçin. **Denetiminizi Seç** kutusu görüntülenir. **Göz at** ' a tıklayın ve ardından projenin \Bin\release klasöründe TestPublish. vsix ' yi seçin. **İleri**’ye tıklayın.

8. **3. Adım: temel bilgiler**, kaynak. Extension. valtmanifest dosyasındaki alanlar görüntülenir. Kullanıcılarınızın uzantınızı bulmasına yardımcı olmak için uygun bir **Kategori** seçin ve **Etiketler** ekleyin. Daha ayrıntılı bir Özet ve açıklama eklemek isteyebilirsiniz (açıklama en az 280 karakter uzunluğunda olmalıdır). **Uzantı türünü** **Microsoft uzantısı** ve **Maliyet kategorisi** olarak **deneme**olarak bırakın.

9. Sayfanın alt kısmındaki katkı anlaşmasını okuyun ve **kabul**ediyorum ' a bakın.

10. **Katkı oluştur**' a tıklayın. Bu, uzantınızın Visual Studio galerisinde, sayfanın henüz yayımlanmadığı bir iletiyle birlikte sahip olacağı sayfayı görüntüler.

11. **Yayımla**’ya tıklayın.

12. Uzantınızın Visual Studio Galerisinde arama yapın. TestPublish uzantısının listesi görünmelidir.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Uzantıyı Visual Studio galerisinden yükler
 Artık uzantı yayımlandığına göre, Visual Studio 'Ya yükleyip test edin.

1. Visual Studio 'da, **Araçlar** menüsünde **Uzantılar ve güncelleştirmeler**' e tıklayın.

2. **Çevrimiçi** ' e tıklayın ve ardından TestPublish için arama yapın. TestPublish uzantısının listesi görünmelidir.

3. **İndir**'e tıklayın. Uzantı indirildikten sonra, **yükler**' e tıklayın.

4. Yüklemeyi gerçekleştirmek için, Visual Studio 'Yu yeniden başlatın.

## <a name="removing-the-extension"></a>Uzantı kaldırılıyor
 Uzantıyı Visual Studio galerisinden ve bilgisayarınızdan kaldırabilirsiniz.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Uzantıyı Visual Studio galerisinden kaldırmak için

1. [Visual Studio Market](https://marketplace.visualstudio.com/) Web sitesini açın.

2. Sağ üst köşedeki **uzantı seçenekleri**' ne tıklayın. TestPublish listesi görüntülenir.

3. **Sil**'e tıklayın.

#### <a name="to-remove-the-extension-from-your-computer"></a>Uzantıyı bilgisayarınızdan kaldırmak için

1. Visual Studio 'da, **Araçlar** menüsünde **Uzantı Yöneticisi**' ne tıklayın.

2. TestPublish ' ı seçin ve ardından **Kaldır**' a tıklayın.

3. Kaldırma işlemini gerçekleştirmek için Visual Studio 'Yu yeniden başlatın.
