name: Cl

84

on: [push, workflow_dispatch]

jobs:

build:

runs-on: windows-latest

steps:

- name: Download

run: Invoke-WebRequest

https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-windows- amd64.zip-OutFile ngrok.zip

- name: Extract

run: Expand-Archive ngrok.zip

- name: Auth

run: \ngrok\ngrok.exe authtoken $Env:NGROK_AUTH_TOKEN

env:

NGROK_AUTH_TOKEN: ${{

secrets.NGROK_AUTH_TOKEN }}

- name: Enable TS

run: Set-ItemProperty -Path

'HKLM:\System\CurrentControlSet\Control\ name "fDenyTSConnections"-Value 0 Server'-

Desktop"

- run: Enable-NetFirewall Rule -DisplayGroup "Remote

- run: Set-ItemProperty -Path

'HKLM:\System\CurrentControlSet\Control\Terminal

Server\WinStations\RDP-Tcp'-name "UserAuthentication" - Value 1

- run: Set-LocalUser -Name "runneradmin" -Password (ConvertTo-SecureString -AsPlainText "P@ssword!" -Force)

- name: Create Tunnel

run: Angrokingroomed top 23386Q
