#!/bin/bash

p="$HOME/.hombrew"
d=$(date +%Y%m%d-%H%M%S)
if [ -d !$HOME/.homebrew/ ]; then
  mkdir $HOME/.homebrew
  mkdir -p $HOME/.homebrew/cask
  mkdir -p $HOME/.homebrew/pkg
fi

cmd="brew ${@}"
for OPT in "$@"
do
	case $OPT in
		--cache)
			shift
			if [ "$1" = "clear" ];then
				shift
				if [ -z "$1" ];then
					rm -f $HOME/.homebrew/pkg/*
					rm -f $HOME/.homebrew/cask/*
				fi
				for i in {$1,$2};do
					if [ "$i" = "--formula" ];then
						rm -f $HOME/.homebrew/pkg/*
					elif [ "$i" = "--cask" ];then
						rm -f $HOME/.homebrew/cask/*
					fi
				done
				exit 1;
			else
				if [ -z "$1" ];then
					cd $HOME/.homebrew/pkg
					brew list --formula | sort -n | tee $d
					cd $HOME/.homebrew/cask
					brew list --cask | sort -n | tee $d
				fi
				for i in {$1,$2};do
					if [ "$i" = "--formula" ];then
						cd $HOME/.homebrew/pkg
						brew list --formula | sort -n | tee $d
					elif [ "$i" = "--cask" ];then
						cd $HOME/.homebrew/cask
						brew list --cask | sort -n | tee $d
					fi
				done
			fi
			exit 1
			;;
		*)
			eval $cmd
			exit 1
			;;
	esac
done

brew
