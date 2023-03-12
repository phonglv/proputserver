  345  git clone https://github.com/DepartureLabsIC/non-fungible-token.git nft
  346  cd nft
  347  dfx start --background
  348  dfx deploy --no-wallet
  349  dfx identity get-principal
  350  dfx canister call nft init '(vec {principal "oy7al-zoh7d-fk4pm-o4agp-imod5-j4y5t-dheoi-qrr3c-dzfri-oc4x3-uqe"}, record {name = "ICPTOWN"; symbol = "ICPTOWN"})'
  351  dfx identity get-principal
  352  dfx identity --network ic get-wallet
  353  dfx identity --network ic balance
  354  dfx deploy --network ic nft --with-cycles 700000000000
  355  dfx identity get-principal
  356  dfx canister --network ic --wallet inrww-miaaa-aaaai-qagta-cai call nft init '(vec {principal "oy7al-zoh7d-fk4pm-o4agp-imod5-j4y5t-dheoi-qrr3c-dzfri-oc4x3-uqe"}, record {name = "ICP TOWN"; symbol = "ICPTOWN"})'
  357  dfx canister --network ic --wallet my-wallet-canister call nft init '(vec {principal "oy7al-zoh7d-fk4pm-o4agp-imod5-j4y5t-dheoi-qrr3c-dzfri-oc4x3-uqe"}, record {name = "ICP TOWN"; symbol = "ICPTOWN"})'
  358  dfx identity --network ic get-wallet
  359  dfx canister --network ic --wallet slb2k-aqaaa-aaaai-qaefq-cai call nft init '(vec {principal "oy7al-zoh7d-fk4pm-o4agp-imod5-j4y5t-dheoi-qrr3c-dzfri-oc4x3-uqe"}, record {name = "ICP TOWN"; symbol = "ICPTOWN"})'
  360  dfx canister --network ic --no-wallet call nft updateContractOwners '(record {user = principal "bu5da-korq2-4rmym-j645m-7l4w5-5a4xc-5dv4l-uto26-b25i7-bdcql-2qe"; isAuthorized = true})'
  361  dfx canister --network ic id
  362  dfx  --network ic canister id nft
  363  dfx canister --network ic id nft
  364  dfx canister --network ic --no-wallet call nft getContractInfo
  365  dfx canister --network ic --no-wallet call nft mint
  366  [A
  367  dfx canister --network ic --no-wallet call nft listAssets()
  368  dfx canister --network ic --no-wallet call nft listAssets


for file in ./*; dfx canister call nft mint "(record {\
    index = $(echo $file | sed -E "s/(\.\/art\/)([0-9]+)\.(png)/\2/");\
    asset = record {\
        contentType = \"image/$(echo $file | sed -E "s/(\.\/art\/)([0-9]+)\.(png)/\3/")\";\
        payload = vec {\
            vec { $(for byte in $(od -v -tuC $file | sed -E "s/[0-9]+//"); echo "$byte;") };\
        };\
    }\
})"

	for byte in $(od -v -tuC $file | sed -E "s/[0-9]+//")
	  do 
	    echo "$byte;"
	  done



	$(dfx canister call nft mint "(
			record {\
				contentType = \"image/$(echo $file | sed -E "s/(\.\/art\/)([0-9]+)\.(png)/\3/")\";\
				payload = vec {\
            		vec {\
					for byte in $(od -v -tuC $file | sed -E "s/[0-9]+//")
					  do 
						echo "$byte;"
					  done
					};\
				};\
    		})\
	)

dfx canister install nft --argument="(\"ICPT NFT\", \"ICPT\", \"ICP Town NFT collection\", principal \"oy7al-zoh7d-fk4pm-o4agp-imod5-j4y5t-dheoi-qrr3c-dzfri-oc4x3-uqe\")"

eval dfx canister --no-wallet install nft --argument="'(\"ICPT NFT\", \"ICPT\", \"ICPT\", \"ICP Town NFT collection\", principal \"$(dfx identity get-principal)\")'"

