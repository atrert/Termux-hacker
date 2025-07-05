# 🛠️ Crear Hacker Menu
mkdir -p ~/HackerMenu
cd ~/HackerMenu

cat > hacker-menu.sh << 'EOF'
#!/bin/bash
clear
echo -e "\e[1;32m============================"
echo -e "     🔥 HACKER MENU 🔥"
echo -e "============================\e[0m"
echo -e "\e[1;33m1) Escaneo de redes (Nmap)"
echo "2) Phishing (Zphisher)"
echo "3) WhatsApp Bot (Baileys)"
echo "4) Descargar videos YouTube"
echo "5) Personalización (Neofetch, Matrix)"
echo "6) Salir"
echo -e "============================\e[0m"
read -p "👉 Elige una opción [1-6]: " opt

case $opt in
  1) 
    pkg install nmap -y
    read -p "📡 Ingresa la IP o rango (ej: 192.168.1.0/24): " ip
    nmap -sn $ip
    ;;
  2)
    pkg install git -y
    git clone https://github.com/htr-tech/zphisher.git ~/HackerMenu/zphisher
    cd ~/HackerMenu/zphisher
    bash zphisher.sh
    ;;
  3)
    pkg install nodejs -y
    git clone https://github.com/adiwajshing/Baileys ~/HackerMenu/Baileys
    cd ~/HackerMenu/Baileys
    npm install
    echo "✅ WhatsApp Bot listo para usar."
    ;;
  4)
    pkg install python -y
    pip install youtube-dl
    read -p "🎥 Pega el link del video: " link
    youtube-dl "$link"
    ;;
  5)
    pkg install neofetch cmatrix lolcat -y
    neofetch
    echo "🎨 Ejecuta 'cmatrix' para efecto Matrix."
    ;;
  6)
    echo "👋 Saliendo..."
    exit
    ;;
  *)
    echo "❌ Opción inválida"
    ;;
esac
EOF

chmod +x hacker-menu.sh
echo 'alias hacker-menu="bash ~/HackerMenu/hacker-menu.sh"' >> ~/.zshrc
source ~/.zshrc

clear
echo "✅ HACKER MENU instalado con éxito. Escribe 👉 hacker-menu" | lolcat
