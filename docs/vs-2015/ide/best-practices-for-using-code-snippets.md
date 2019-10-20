---
title: Kod parçacıkları kullanmak için en iyi uygulamalar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 74da305b69a9561573466d385c5d7b686da3693f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620320"
---
# <a name="best-practices-for-using-code-snippets"></a>Kod Parçacıkları İçin En İyi Uygulamalar
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod parçacığındaki kod yalnızca bir şeyi yapmanın en temel yolunu gösterir. Çoğu uygulama için, kodun uygulamaya uyacak şekilde değiştirilmesi gerekir.

## <a name="handling-exceptions"></a>Özel Durumları İşleme
 Genellikle kod parçacığı dene... Catch blokları, tüm özel durumları yakalar ve yeniden oluşturur. Bu, projeniz için doğru seçim olmayabilir. Her özel durum için, yanıt vermenin birkaç yolu vardır. Örnekler için bkz. [nasıl yapılır: try/catch kullanarak özel durum işleme (C# Programlama Kılavuzu)](https://msdn.microsoft.com/library/ca8e3773-980e-4767-8633-7408540e9818) ve [TRY... Yakala... Finally ekstresi](https://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b).

## <a name="file-locations"></a>Dosya konumları
 Dosya konumlarını uygulamanıza uyardığınızda, aşağıdakilere göz önünde bulundurun:

- Erişilebilir bir konum bulma. Kullanıcıların, bilgisayarın Program Files klasörüne erişimi olmayabilir, bu nedenle dosyaları uygulama dosyalarıyla depolamak çalışmayabilir.

- Güvenli bir konum bulma. Dosyaların kök klasörde depolanması (C: \\) güvenli değildir. Uygulama verileri için \Application Data klasörünü öneririz. Uygulama, bireysel kullanıcı verileri için, her kullanıcı için \Documents klasöründe bir dosya oluşturabilir.

- Geçerli bir dosya adı kullanılıyor. Geçersiz dosya adlarının olasılığını azaltmak için <xref:System.Windows.Forms.OpenFileDialog> ve <xref:System.Windows.Forms.SaveFileDialog> denetimlerini kullanabilirsiniz. Kullanıcının bir dosyayı seçtiği zaman ve kodunuzun dosyayı ne zaman kullandığı zaman arasında, dosyanın silinmiş olabileceğini unutmayın. Ayrıca, kullanıcının dosyaya yazma izni olmayabilir.

## <a name="security"></a>Güvenlik
 Bir parçacığı güvenli hale getirme, kaynak kodda kullanıldığı yere ve kodda olduktan sonra nasıl değiştirildiği üzerine bağlıdır. Aşağıdaki liste, göz önünde bulundurulması gereken birkaç alanı içerir.

- Dosya ve veritabanı erişimi

- Kod erişim güvenliği

- Kaynakları koruma (olay günlükleri, kayıt defteri)

- Gizli dizileri depolama

- Girişleri doğrulama

- Verileri kodlama teknolojilerine geçirme

  Daha fazla bilgi için bkz. [uygulamaları güvenli hale getirme](../ide/securing-applications.md).

## <a name="downloaded-code-snippets"></a>İndirilen kod parçacıkları
 Visual Studio tarafından yüklenen IntelliSense kod parçacıkları kendi kendine güvenlik tehlikesi içinde değildir. Ancak, uygulamanızda güvenlik riskleri oluşturabilir. Internet 'ten indirilen kod parçacıkları, çok dikkatli bir şekilde indirilen diğer içerikler gibi değerlendirilmelidir.

- Yalnızca güvendiğiniz sitelerden kod parçacıklarını indirin ve güncel virüs yazılımlarını kullanın.

- İndirilen tüm kod parçacığı dosyalarını Not defteri 'nde veya Visual Studio 'nun XML düzenleyicisinde açın ve yüklemeden önce dikkatlice gözden geçirin. Aşağıdaki sorunları arayın:

  - Kod parçacığı kodu, çalıştırırsanız sisteminize zarar verebilir. Kaynak kodunu çalıştırmadan önce dikkatle okuyun.

  - Kod parçacığı dosyasının yardım URL bloğu, kötü amaçlı betik dosyası çalıştıran veya saldırgan bir Web sitesi görüntüleyen URL 'Leri içerebilir.

  - Kod parçacığında projenize sessizce eklenen ve sisteminizde herhangi bir yerden yüklenebilecek başvurular bulunabilir. Bu başvurular, kod parçacığını indirdiğiniz bilgisayardan bilgisayarınıza indirilmiş olabilir. Kod parçacığı daha sonra, başvuru içindeki kötü amaçlı kodu yürüten bir yönteme çağrı yapabilir. Bunu böyle bir saldırıya karşı korumak için, kod parçacığı dosyasının Içeri aktarmaları ve başvuru bloklarını gözden geçirin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Basic IntelliSense kod parçacıkları](https://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643) uygulamalar [kod parçacıklarını](../ide/code-snippets.md) [güvenli hale getirme](../ide/securing-applications.md)
