---
title: "Nasıl yapılır: Visual Studio 'Yu dağıtmaya yönelik ürün anahtarlarını otomatik olarak uygulama 2015 | Microsoft Docs"
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 11
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ec050cf8f365bfae2290593a0c7f215dcb2f39cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186003"
---
# <a name="how-to-automatically-apply-product-keys-when-deploying-visual-studio"></a>Nasıl Yapılır: Visual Studio’yu dağıtırken ürün anahtarlarını otomatik olarak uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [Visual Studio 'yu dağıttığınızda ürün anahtarlarını otomatik olarak uygulama](/visualstudio/install/automatically-apply-product-keys-when-deploying-visual-studio).

Visual Studio 2015 dağıtımını otomatik hale getirmek için kullanılan bir betiğin parçası olarak ürün anahtarınızı programlı bir şekilde uygulayabilirsiniz. Ürün anahtarları, Visual Studio yüklemesi sırasında veya yükleme tamamlandıktan sonra bir cihazda program aracılığıyla ayarlanabilir.

## <a name="apply-the-license-during-installation"></a>Yükleme sırasında lisansı uygulama
 Visual Studio 'nun kurulum işlemi sırasında bir ürün anahtarı uygulamak için/ProductKey parametresini kullanın. Bu kurulum parametresi, bir son kullanıcı için zaten lisanslı bir durumda Visual Studio 'Yu yüklemek üzere/Silent parametresiyle birlikte kullanılabilir. /ProductKey parametresini kullanmak için bir komut istemi açın. Kurulum programını çalıştırın (örneğin, vs_enterprise.exe veya vs_professional.exe) ve/ProductKey parametresini tire içermeyen bir ürün anahtarı (25 karakter) ile ayarlayın:

 Bu, Visual Studio 2015 Enterprise 'ı AAAAABBBBBCCCCCDDDDDEEEEEEE ürün anahtarı ile yüklemeye yönelik örnek bir komuttur:

 `vs_enterprise.exe [any other setup parameters] /ProductKey AAAAABBBBBCCCCCDDDDDDEEEEEE`

## <a name="apply-the-license-after-installation"></a>Yüklemeden sonra lisansı Uygula
 Hedef makinelerdeki storePID.exe yardımcı programını sessiz modda kullanarak, Visual Studio 'nun yüklü bir sürümünü ürün anahtarıyla etkinleştirebilirsiniz. StorePID.exe, Visual Studio ** \<drive> : \\ \Program Files (x86) \Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe**ile yüklenen bir yardımcı programdır.

 Bir System Center Aracısı veya yükseltilmiş bir komut istemi kullanarak, yükseltilmiş ayrıcalıklarla storePID.exe çalıştırın, ardından ürün anahtarı (Tireler dahil) ve Microsoft ürün kodu (MPC) kullanın. Ana çizgileri ürün anahtarına eklediğinizden emin olun!

 `StorePID.exe [product key including the dashes] [MPC]`

 Bu, bir ürün anahtarı "AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE" içeren Visual Studio 2015 Enterprise 07060 'ı yüklemek için örnek bir komut satırı örneğidir:

 `C:\Program Files (x86)\Microsoft Visual Studio 14.0\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 07060`

 Aşağıdaki tabloda, Visual Studio 'nun her sürümü için MPC kodları listelenmektedir:

|Visual Studio sürümü|MPC|
|---------------------------|---------|
|Visual Studio Enterprise 2015|07060|
|Visual Studio Professional 2015|07062|
|Visual Studio Test Professional 2015|07066|
|Visual Studio Ultimate 2013|06181|
|Visual Studio Premium 2013|06191|
|Visual Studio Professional 2013|06177|
|Visual Studio Test Professional 2013|06194|

Ürün anahtarı alma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio ürün anahtarını bulma](../install/how-to-locate-the-visual-studio-product-key.md).

StorePID.exe ürün anahtarını başarıyla uyguladıysanız, 0 döndürür. Hatalarla karşılaşırsa, 1 ile 6 arasında bir sayı döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'yu yükleme](../install/install-visual-studio-2015.md)