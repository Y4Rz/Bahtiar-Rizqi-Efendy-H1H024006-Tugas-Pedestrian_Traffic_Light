
// SETUP PIN

// Lampu kendaraan
int merahK = 2;   // LED merah kendaraan di pin 2
int kuningK = 3;  // LED kuning kendaraan di pin 3
int hijauK = 4;   // LED hijau kendaraan di pin 4

// Lampu pedestrian (penyeberang)
int merahP = 5;   // LED merah pedestrian di pin 5
int hijauP = 6;   // LED hijau pedestrian di pin 6

// Tombol
int tombol = 7;   // Push button di pin 7

// Variabel kontrol
bool proses = false; // Menyimpan status apakah sistem sedang berjalan atau tidak


// SETUP (DIJALANKAN SEKALI)
void setup() {

  // Mengatur semua pin LED sebagai OUTPUT
  pinMode(merahK, OUTPUT);
  pinMode(kuningK, OUTPUT);
  pinMode(hijauK, OUTPUT);

  pinMode(merahP, OUTPUT);
  pinMode(hijauP, OUTPUT);

  // Mengatur tombol sebagai INPUT dengan pull-up internal
  pinMode(tombol, INPUT_PULLUP);

  // KONDISI AWAL

  // Kendaraan boleh jalan (lampu hijau nyala)
  digitalWrite(hijauK, HIGH);
  digitalWrite(merahK, LOW);
  digitalWrite(kuningK, LOW);

  // Pedestrian berhenti (lampu merah nyala)
  digitalWrite(merahP, HIGH);
  digitalWrite(hijauP, LOW);
}

// LOOP (DIJALANKAN TERUS)
void loop() {

  // Cek apakah tombol ditekan (LOW karena pakai pull-up)
  // dan sistem tidak sedang dalam proses
  if (digitalRead(tombol) == LOW && !proses) {

    proses = true; // Tandai bahwa sistem sedang berjalan

    // KENDARAAN BERHENTI
    digitalWrite(hijauK, LOW);   // Matikan hijau kendaraan
    digitalWrite(merahK, HIGH);  // Nyalakan merah kendaraan

    // PEDESTRIAN MENYEBRANG
    digitalWrite(merahP, LOW);   // Matikan merah pedestrian
    digitalWrite(hijauP, HIGH);  // Nyalakan hijau pedestrian

    delay(5000); // Waktu penyeberang (5 detik)

    // PEDESTRIAN SELESAI
    digitalWrite(hijauP, LOW);   // Matikan hijau pedestrian
    digitalWrite(merahP, HIGH);  // Nyalakan merah pedestrian

    // TRANSISI KENDARAAN (KUNING)
    digitalWrite(merahK, LOW);   // Matikan merah kendaraan

    // Lampu kuning berkedip 5 kali
    for (int i = 0; i < 5; i++) {
      digitalWrite(kuningK, HIGH); // Nyalakan kuning
      delay(500);                  // Tunggu 0.5 detik
      digitalWrite(kuningK, LOW);  // Matikan kuning
      delay(500);                  // Tunggu 0.5 detik
    }

    // KEMBALI KE KONDISI AWAL
    digitalWrite(hijauK, HIGH); // Kendaraan jalan lagi (hijau nyala)

    proses = false; // Reset status agar tombol bisa digunakan lagi
  }
}
