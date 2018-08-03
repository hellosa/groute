# groute
The faster route command for linux written in Go.

### usage:
	# acquire the network lib
	go get github.com/vishvananda/netlink
	
	# compile the go program
	go build groute.go
	
	# run groute as root (it works no matter it's an ip or a file)
	# an ip such as 8.8.8.8
	sudo ./groute add 8.8.8.8/32 $(gateway_ip)
	
	# a file named chinaipv4.txt
	sudo ./groute add chinaipv4.txt $(gateway_ip)
	
	# del/delete also works
	sudo ./groute del 8.8.8.8/32 $(gateway_ip)
	
#### Equivalent to:

	# if you use iproute2
	sudo ip route add 8.8.8.8/32 via $(gateway_ip)
	
	# and
	for line in `cat chinaipv4.txt`
	do
		sudo ip route add $line via $(gateway_ip)
	done
	
	# and
	sudo ip route del 8.8.8.8/32 via $(gateway_ip)
