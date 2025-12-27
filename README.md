# Replace this with your direct image URL
$url = "https://upload.wikimedia.org/wikipedia/commons/thumb/8/85/Flag_of_Belarus.svg/250px-Flag_of_Belarus.svg.png"

# Where to save the image
$path = "$env:USERPROFILE\Pictures\wallpaper.jpg"

# Download the image
Invoke-WebRequest -Uri $url -OutFile $path

# Set wallpaper registry values
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name Wallpaper -Value $path
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name WallpaperStyle -Value 10  # Fill
Set-ItemProperty -Path "HKCU:\Control Panel\Desktop" -Name TileWallpaper -Value 0

# Apply the wallpaper
rundll32.exe user32.dll, UpdatePerUserSystemParameters
