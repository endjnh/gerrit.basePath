using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Btchuong3
{
    internal class Class1
    {
        public class PhanSo
        {
            public int TuSo { get; set; }
            public int MauSo { get; set; }

            public PhanSo(int tuSo, int mauSo)
            {
                TuSo = tuSo;
                MauSo = mauSo;
            }

            public static PhanSo Hieu(PhanSo a, PhanSo b)
            {
                int tuSo = a.TuSo * b.MauSo - a.MauSo * b.TuSo;
                int mauSo = a.MauSo * b.MauSo;
                return new PhanSo(tuSo, mauSo);
            }

            public void ToiGian()
            {
                int ucln = UCLN(this.TuSo, this.MauSo);
                this.TuSo /= ucln;
                this.MauSo /= ucln;
            }

            private static int UCLN(int a, int b)
            {
                while (b != 0)
                {
                    int temp = b;
                    b = a % b;
                    a = temp;
                }
                return Math.Abs(a);
            }
        }

        public class QLPhanSo : PhanSo
        {
            private PhanSo[] arr;

            public QLPhanSo(int tuSo, int mauSo, PhanSo[] arr) : base(tuSo, mauSo)
            {
                this.arr = arr;
            }

        }
        class Program
        {
            private static void Main(string[] args)
            {
                PhanSo ps1 = new PhanSo(3, 4);
                PhanSo ps2 = new PhanSo(5, 6);

                PhanSo hieu = PhanSo.Hieu(ps1, ps2);
                Console.WriteLine("Hiệu của hai phân số là: " + hieu.TuSo + "/" + hieu.MauSo);

                hieu.ToiGian();
                Console.WriteLine("Dạng tối giản của hiệu hai phân số là: " + hieu.TuSo + "/" + hieu.MauSo);

            }
        }

    }
}
