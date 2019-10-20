---
title: Birim testleri oluşturmak için örnek proje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d495d0bf12c900d34a04a84e950b002494b7b5c3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660403"
---
# <a name="sample-project-for-creating-unit-tests"></a>Birim Testleri Oluşturmak için Örnek Proje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu örnek kod aşağıdaki izlenecek yollarda kullanılmak üzere verilmiştir:

- [Izlenecek yol: yönetilen kod Için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Bu izlenecek yol, birim testlerini oluşturma ve özelleştirme, çalıştırma ve test sonuçlarını inceleme adımlarında size yol gösterir.

- [Izlenecek yol: testleri çalıştırın ve kod kapsamını görüntüleyin](https://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8). Bu izlenecek yol, projenin test edilmekte olan kodunun oranını gösteren kod kapsamı verilerinin nasıl görüntüleneceğini gösterir.

- [Izlenecek yol: komut satırı test yardımcı programını kullanma](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867). Bu izlenecek yolda, testleri çalıştırmak ve sonuçları görüntülemek için MSTest. exe komut satırı yardımcı programını kullanın.

## <a name="sample-code"></a>Örnek kod
 Bu örnekteki tek bilerek oluşan hata, "m_balance + = amount" ın kredisin, eşittir işaretinden önceki bir artı işareti olmaması gerekir.

```
using System;

namespace BankAccountNS
{
    /// <summary>
    /// Bank Account demo class.
    /// </summary>
    public class BankAccount
    {
        private string m_customerName;

        private double m_balance;

        private bool m_frozen = false;

        private BankAccount()
        {
        }

        public BankAccount(string customerName, double balance)
        {
            m_customerName = customerName;
            m_balance = balance;
        }

        public string CustomerName
        {
            get { return m_customerName; }
        }

        public double Balance
        {
            get { return m_balance; }
        }

        public void Debit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount > m_balance)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount; // intentionally incorrect code
        }

        public void Credit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount;
        }

        private void FreezeAccount()
        {
            m_frozen = true;
        }

        private void UnfreezeAccount()
        {
            m_frozen = false;
        }

        public static void Main()
        {
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

            ba.Credit(5.77);
            ba.Debit(11.22);
            Console.WriteLine("Current balance is ${0}", ba.Balance);
        }

    }
}
```

 /* Örnek şirketler, kuruluşlar, ürünler, etki alanı adları, e-posta adresleri, logolar, kişiler, konumlar ve burada adı geçen olaylar hayalidir.  Herhangi bir gerçek şirket, kuruluş, ürün, etki alanı adı, e-posta adresi, logo, kişi, yer veya olay ile ilişki amaçlanmamıştır. \*/

## <a name="working-with-the-code"></a>Kodla çalışma
 Bu kodla çalışmak için öncelikle [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] için bir proje oluşturmanız gerekir. [Izlenecek yol: yönetilen kod Için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)konusunun "Izlenecek yolu hazırlama" bölümündeki adımları izleyin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Izlenecek yol: yönetilen kod Için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) [izlenecek yol: testleri çalıştırma ve kod kapsamını görüntüleme](https://msdn.microsoft.com/d4aab8e2-2140-4975-b4e3-41ef3fa944c8) [izlenecek yol: komut satırı test yardımcı programını kullanma](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867)
