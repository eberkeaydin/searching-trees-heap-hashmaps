using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Project3
{
    class Program
    {
        static Random r = new Random();
        static void Main(string[] args)
        {
            // 1.a
            String[] duraklar = { "İnciraltı, 28, 2, 10", "Sahilevleri, 8, 1, 11", "Doğal Yaşam Parkı, 17, 1, 6",
                "Bostanlı İskele, 7, 0, 5", "Buz Pisti , 11, 0, 9", "Hasanağa Parkı, 7, 0, 5",
                "Alsancak İskele, 8, 5, 3", "Fuar Montrö, 8, 7, 1", "Karataş, 7, 0, 8"};
            List<Durak> durakNesneler = new List<Durak>(); 

            foreach (string durak in duraklar) //duraklar arrayinden bilgileri çekip istenen random müşteri bilgileri tutuldu.
            {
                string[] splitNesne = durak.Split(",");
                List<Müsteri> müşteriler = new List<Müsteri>(20);
                int randomMusteriSay = r.Next(1, 10);
                if (randomMusteriSay > (Int32.Parse(splitNesne[2]) + Int32.Parse(splitNesne[3])))
                {
                    randomMusteriSay = Int32.Parse(splitNesne[2]) + Int32.Parse(splitNesne[3]);
                }

                for (int j = 0; j < randomMusteriSay; j++)
                {
                    int müsID = r.Next(1, 21);
                    int s = r.Next(1, 25);
                    int d = r.Next(1, 61);
                    Zaman zmn = new Zaman(s, d); // Zaman sınıfından obje yaratıldı
                    Müsteri m = new Müsteri(müsID, zmn);
                    müşteriler.Add(m);

                }

                durakNesneler.Add(new Durak(splitNesne[0], Int32.Parse(splitNesne[1]), Int32.Parse(splitNesne[2]), Int32.Parse(splitNesne[3]), müşteriler));
                // Veriler listeye gönderildi

            }
            DurakAğacı bt = new DurakAğacı();

            foreach (Durak x in durakNesneler) //Oluşturduğumuz Generic ile tüm nesneleri burdan ağaca attık
            {
                bt.insert(x);
            }

            bt.updateTree(bt.getRoot());
            // 1.b
            Console.WriteLine("Ağacın Derinliği: " + bt.getMaxDepth(bt.getRoot()));
            Console.WriteLine();
            Console.WriteLine("Ağaçtaki Tüm Bilgiler; ");
            Console.WriteLine();
            bt.preOrder(bt.getRoot());

            // 1.c
            Console.WriteLine("Kiralama bilgilerini görmek istediğiniz Müşteri ID: ");
            int mID = Convert.ToInt32(Console.ReadLine());

            bt.getMüşteriInfo(mID, bt.getRoot());

            // 1.d
            Console.WriteLine("Normal bisiklet kiralama;");
            Console.WriteLine("Müşteri ID: ");
            int id = Convert.ToInt32(Console.ReadLine());
            Console.WriteLine("Durak adı: ");
            string da = Console.ReadLine();
            bt.normalKiralama(da, id, bt.getRoot());

            // 2.a
            Hashtable hash = new Hashtable();
            foreach (string s in duraklar) // Duraklar listesinden gerekli bilgiler çekilip key- value olarak hash'e aktarıldı
            {
                string[] keysNvalues = s.Split(",");
                int[] durakBilgileri = { Convert.ToInt32(keysNvalues[1]), Convert.ToInt32(keysNvalues[2]), Convert.ToInt32(keysNvalues[3]) };
                hash.Add(keysNvalues[0], durakBilgileri);
            }


            // 2.b
            foreach (string str in duraklar) // Boş park sayısı 5ten büyük olan parklar için güncelleme yapıldı
            {
                string[] keysNvalues = str.Split(",");
                if (Convert.ToInt32(keysNvalues[1]) > 5)
                {
                    int a = Convert.ToInt32(keysNvalues[3]);
                    a += 5;
                    keysNvalues[3] = Convert.ToString(a);
                    int[] durakBilgileri = { Convert.ToInt32(keysNvalues[1]), Convert.ToInt32(keysNvalues[2]), Convert.ToInt32(keysNvalues[3]) };
                    hash[keysNvalues[0]] = durakBilgileri;
                }

            }

        }
        class Durak // Yapılandırıcı sınıf 
        {
            string durakAdi;
            int bos_park_say;
            int tandem_say;
            int normal_say;
            List<Müsteri> müsteriList = new List<Müsteri>();

            public Durak(string durak, int bos_park, int tandem, int normal, List<Müsteri> m)
            {
                this.durakAdi = durak;
                this.bos_park_say = bos_park;
                this.tandem_say = tandem;
                this.normal_say = normal;
                this.müsteriList = m;
            }


            public string getDurakAdi()
            {
                return durakAdi;
            }

            public int getBosPark()
            {
                return bos_park_say;
            }
            public void setBosPark(int bPark) { this.bos_park_say = bPark; } // Güncelleme için
            public int getTandem()
            {
                return tandem_say;
            }
            public void setTandem(int tndm) { this.tandem_say = tndm; }
            public int getNormal()
            {
                return normal_say;
            }
            public void setNormal(int nrml) { this.normal_say = nrml; }

            public int getListSize() { return müsteriList.Count; }
            public List<Müsteri> getList() { return this.müsteriList; }

        }
        class TreeNode
        {
            public Durak data;
            public TreeNode leftChild;
            public TreeNode rightChild;



            public void displayNode()
            {
                Console.Write("Durak Adı: " + data.getDurakAdi() + "\n"
                            + "Boş Park Yeri:  " + data.getBosPark() + "\n"
                            + "Tandem Bisiklet Sayısı: " + data.getTandem() + "\n"
                            + "Normal Bisiklet Sayısı:  " + data.getNormal() + "\n"
                            + "Kiralama İşlemi Yapan Müşteri Sayısı: " + data.getListSize() + "\n");

                Console.WriteLine();
                Console.WriteLine("Müşteri Bilgileri; ");
                Console.WriteLine();

                foreach (Müsteri m in data.getList())
                {
                    Console.Write("Müşteri ID: " + m.getMüşteriID() + "\n"
                                + m.getZaman().toString());
                }

                Console.WriteLine();
            }


        }
        class DurakAğacı
        {
            private TreeNode root;
            private int size;

            public DurakAğacı() { root = null; }

            public TreeNode getRoot()
            { return root; }

            // Agacın preOrder Dolasılması
            public void preOrder(TreeNode localRoot)
            {
                if (localRoot != null)
                {
                    localRoot.displayNode();
                    preOrder(localRoot.leftChild);
                    preOrder(localRoot.rightChild);
                }
            }

            // Agacın inOrder Dolasılması
            public void inOrder(TreeNode localRoot)
            {
                if (localRoot != null)
                {
                    inOrder(localRoot.leftChild);
                    localRoot.displayNode();
                    inOrder(localRoot.rightChild);
                }
            }

            // Agacın postOrder Dolasılması
            public void postOrder(TreeNode localRoot)
            {
                if (localRoot != null)
                {
                    postOrder(localRoot.leftChild);
                    postOrder(localRoot.rightChild);
                    localRoot.displayNode();
                }
            }

            // Agaca bir dügüm eklemeyi saglayan metot
            public void insert(Durak newdata)
            {
                TreeNode newNode = new TreeNode();
                newNode.data = newdata;
                if (root == null)
                    root = newNode;

                else
                {
                    TreeNode current = root;
                    TreeNode parent;
                    while (true)
                    {
                        parent = current;
                        if (string.Compare(newdata.getDurakAdi(), current.data.getDurakAdi()) < 0)
                        {
                            current = current.leftChild;
                            if (current == null)
                            {
                                parent.leftChild = newNode;
                                return;
                            }
                        }
                        else
                        {
                            current = current.rightChild;
                            if (current == null)
                            {
                                parent.rightChild = newNode;
                                return;
                            }
                        }
                    } // end while
                } // end else not root
                size++;
            } // end insert()

            public void updateTree(TreeNode localRoot) // Eklenen müşteri bilgileri ve kiralanan bisiklet sayılarından dolayı ağaç güncellemede kullanıldı
            {
                if (localRoot != null)
                {
                    for (int i = 0; i < localRoot.data.getListSize(); i++)
                    {
                        localRoot.data.setBosPark(localRoot.data.getBosPark() + 1);
                        if (localRoot.data.getNormal() != 0) { localRoot.data.setNormal(localRoot.data.getNormal() - 1); }
                        else { localRoot.data.setTandem(localRoot.data.getTandem() - 1); }
                    }
                    updateTree(localRoot.leftChild);
                    updateTree(localRoot.rightChild);
                }

            }

            public int getMaxDepth(TreeNode localRoot) // Ağaç derinliği bulmak için
            {
                if (localRoot == null)
                    return 0;
                else
                {

                    int leftDepth = getMaxDepth(localRoot.leftChild);
                    int rightDepth = getMaxDepth(localRoot.rightChild);


                    if (leftDepth > rightDepth)
                        return (leftDepth + 1);
                    else
                        return (rightDepth + 1);
                }

            }
            public int getSize()
            {
                return size;
            }

            public void getMüşteriInfo(int ID, TreeNode localRoot) // ID'si verilen müşterinin kiralama bilgileri için kullanılan metot
            {
                if (localRoot != null)
                {
                    foreach (Müsteri m in localRoot.data.getList())
                    {
                        if (m.getMüşteriID() == ID)
                        {
                            Console.WriteLine("Bisiklet kiralanan durak adı: " + localRoot.data.getDurakAdi());
                            Console.WriteLine("Bisikletin kiralandığı saat: " + m.getZaman().toString());
                        }
                    }
                    getMüşteriInfo(ID, localRoot.leftChild);
                    getMüşteriInfo(ID, localRoot.rightChild);
                }
            }

            public void normalKiralama(string ad, int ID, TreeNode localRoot) // Normal bisiklet kiralamak isteyenler için kullanılan metot
            {
                if (localRoot != null)
                {
                    if (ad == localRoot.data.getDurakAdi())
                    {
                        int st = r.Next(25);
                        int dk = r.Next(61);
                        Zaman zaman = new Zaman(st, dk);
                        Müsteri mu = new Müsteri(ID, zaman);
                        localRoot.data.getList().Add(mu);
                        localRoot.data.setBosPark(localRoot.data.getBosPark() + 1);
                        localRoot.data.setNormal(localRoot.data.getNormal() - 1);
                        return;

                    }
                    normalKiralama(ad, ID, localRoot.leftChild);
                    normalKiralama(ad, ID, localRoot.rightChild);
                }
            }
        }

        class Müsteri
        {
            int MüşteriID;
            Zaman zaman;

            public Müsteri(int mID, Zaman z)
            {
                this.MüşteriID = mID;
                this.zaman = z;
            }

            public int getMüşteriID()
            {
                return MüşteriID;
            }
            public Zaman getZaman()
            {
                return zaman;
            }


        }

        class Zaman
        {
            int saat;
            int dakika;

            public Zaman(int sa, int dk)
            {
                this.saat = sa;
                this.dakika = dk;
            }
            public int getSaat()
            {
                return saat;
            }
            public int getDakika()
            {
                return dakika;
            }
            public string toString() // Displayde rahatça kullanabilmek için 
            {
                return "Kiralama saati: " + this.saat + ":" + this.dakika + "\n";
            }

        }




    }

}
