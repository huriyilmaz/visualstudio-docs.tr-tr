---
title: Üçüncü taraf birim testi çerçeveleri 'ni yükler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 12
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bd087dc0b06cbf8ffe4c08f84d819e8ef1c2f8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660520"
---
# <a name="install-third-party-unit-test-frameworks"></a>Nasıl yapılır: Üçüncü taraf birim test çerçevelerini yükleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Test Gezgini, gezgin için bir bağdaştırıcı arabirimi geliştiren herhangi bir birim test çerçevesini çalıştırabilir. Framework 'ün yükleme programı ikili dosyaları yükler ve desteklediği diller için Visual Studio proje şablonları ekler. Şablonuyla bir proje oluşturduğunuzda, çerçeve test Gezgini ile kaydedilir. Visual Studio çözümü, farklı çerçeveleri kullanan ve farklı dillerde hedeflenen birim testi projeleri içerebilir. Test Gezgini tümünü çalıştırır.

 **Requirements**

- Visual Studio Enterprise, Visual Studio Professional

## <a name="acquiring-third-party-frameworks"></a>Üçüncü taraf çerçeveler alınıyor
 Visual Studio Uzantı Yöneticisi ' ni kullanarak veya MSDN Web sitesindeki Visual Studio Galerisi ' nden birçok üçüncü taraf birim testi çerçevesini indirebilir ve yükleyebilirsiniz. Çerçeveler ayrıca Framework 'ün Web sitesi gibi diğer sitelerden de indirilebilir.

### <a name="installing-from-visual-studio"></a>Visual Studio 'dan yükleme

1. Standart menüdeki **Araçlar** ' ı seçin ve ardından **Uzantılar ve güncelleştirmeler**' i seçin.

2. **Çevrimiçi**, **Visual Studio Galerisi**, **Araçlar**' ı genişletin. **Test**' i seçin.

3. Çerçeveyi bulmak için listeyi inceleyin.

4. Çerçeveyi seçin ve **İndir**' i seçin.

   Daha fazla bilgi için bkz. [Visual Studio uzantılarını bulma ve kullanma](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="installing-from-the-web"></a>Web 'den yükleme
 İlgilendiğiniz çerçeveyi biliyorsanız:

1. [Visual Studio Market](https://marketplace.visualstudio.com)açın.

2. **Bul** kutusuna çerçevenin adını yazın.

3. Araç için Visual Studio Galerisi sayfasına gitmek üzere sonuçlar listesinden çerçeveyi seçin.

   Diğer test araçlarıyla birlikte bir çerçeve listesine gitmek için:

4. [Visual Studio Market](https://marketplace.visualstudio.com)açın.

5. **Araştır**' ı seçin.

6. **Kategori** listesinde, **Araçlar** düğümünü genişletin ve ardından **Test**' i seçin.

7. Araç için bir Visual Studio Galerisi sayfasına gitmek üzere sonuçlar listesinde bir çerçeve seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Kodunuza Birim Testi Uygulama](../test/unit-test-your-code.md)
