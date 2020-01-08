---
title: Kod Parçacıkları İçin En İyi Uygulamalar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08add20b59e3e14897d1870aa45fd6cce8698d96
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591716"
---
# <a name="best-practices-for-using-code-snippets"></a>Kod parçacıkları kullanmak için en iyi uygulamalar

Kod parçacığındaki kod yalnızca bir şeyi yapmanın en temel yolunu gösterir. Çoğu uygulama için, kodun uygulamaya uyacak şekilde değiştirilmesi gerekir.

## <a name="handling-exceptions"></a>Özel durumları işleme

Genellikle kod parçacığı dene... Catch blokları, tüm özel durumları yakalar ve yeniden oluşturur. Bu, projeniz için doğru seçim olmayabilir. Her özel durum için, yanıt vermenin birkaç yolu vardır. Örnekler için bkz. [nasıl yapılır: try/catch kullanarak özel durum işleme (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) ve [TRY... Yakala... Finally ekstresi (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Dosya konumları

Dosya konumlarını uygulamanıza uyardığınızda, aşağıdakilere göz önünde bulundurun:

- Erişilebilir bir konum bulma. Kullanıcıların, bilgisayarın *Program Files* klasörüne erişimi olmayabilir, bu nedenle dosyaları uygulama dosyalarıyla depolamak çalışmayabilir.

- Güvenli bir konum bulma. Dosyaların kök klasörde depolanması (*C:\\* ) güvenli değildir. Uygulama verileri için *uygulama verileri* klasörünü öneririz. Uygulama, bireysel kullanıcı verileri için *Belgeler* klasöründeki her bir kullanıcı için bir dosya oluşturabilir.

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

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic IntelliSense kod parçacıkları](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Uygulamaların güvenliğini sağlama](../ide/securing-applications.md)
- [Kod parçacıkları](../ide/code-snippets.md)
